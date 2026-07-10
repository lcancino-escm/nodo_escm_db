# IDE-ESCM — Infraestructura de Datos Espaciales en Docker

Stack completo para publicar geoservicios institucionales cumpliendo estándares
OGC (WMS/WFS) e ISO de metadatos, con una capa propia en Python para reglas
de negocio y control de clasificación de datos (público / restringido / militar).

## Arquitectura

| Componente   | Función                                             | Puerto |
|--------------|------------------------------------------------------|--------|
| PostGIS      | Base de datos espacial (PostgreSQL + extensión GIS)  | 5432   |
| GeoServer    | Publica WMS / WFS / WCS en tiempo real                | 8080   |
| GeoNetwork   | Catálogo de metadatos ISO 19115/19139                | 8081   |
| API (FastAPI)| Orquestación en Python, reglas propias de la ESCM     | 8000   |
| Nginx        | Punto único de entrada / futura terminación SSL       | 80     |

Todo corre en contenedores Docker sobre una única red interna (`ide_net`),
de forma que el servidor Ubuntu queda como host físico/VM con control total
sobre qué puertos se exponen a Internet y cuáles quedan solo internos.

---

## 1. Requisitos del servidor Ubuntu

### Escenario MVP (producción inicial)

- Ubuntu Server 22.04 LTS o 24.04 LTS, **sin interfaz gráfica**
- 4 vCPU, 8 GB RAM
- 100 GB SSD/NVMe (el cuello de botella de PostGIS es IOPS, no espacio — evitar HDD mecánico)
- IP pública fija + dominio institucional (ej. `ide.escm.undef.edu.ar`)

### Escenario "soporte institucional" (a ~1 año, con rasters/imágenes satelitales)

- 8 vCPU, 16–32 GB RAM
- 200 GB SSD/NVMe para SO + PostGIS + contenedores, más almacenamiento en frío
  (HDD u objeto tipo S3) para series históricas de imágenes satelitales pesadas

### Distribución de RAM del stack (ajustado en `docker-compose.yml` con `mem_limit`)

| Servicio    | RAM asignada | Motivo                                                        |
|-------------|-------------:|-----------------------------------------------------------------|
| PostGIS     | 2 GB         | `shared_buffers`/`effective_cache_size` tuneados para consultas espaciales |
| GeoServer   | 3 GB         | JVM heap 2.5 GB + margen para caché de teselas fuera del heap  |
| GeoNetwork  | 1 GB         | Tomcat + catálogo de metadatos                                  |
| API Python  | 256 MB       | FastAPI, uso liviano                                             |
| Nginx       | 128 MB       | Proxy reverso                                                    |
| **Total**   | **~6.4 GB**  | Deja margen para el SO en un host de 8 GB                       |

Estos valores ya están puestos en `docker-compose.yml` (`mem_limit` y `cpus` por
servicio). Si el servidor real termina siendo el escenario "soporte
institucional" (16–32 GB), subí `MAXIMUM_MEMORY` de GeoServer y `shared_buffers`
de PostGIS proporcionalmente — son los dos que más se benefician de RAM extra.

- Acceso root o sudo al servidor

## 2. Instalar Docker y Docker Compose

```bash
sudo apt update && sudo apt upgrade -y

# Docker Engine
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# Permite correr docker sin sudo (cerrar sesión y volver a entrar después)
sudo usermod -aG docker $USER

# Verificar
docker --version
docker compose version
```

## 3. Copiar el proyecto al servidor

Subí la carpeta `ide-escm/` al servidor (por `scp`, `git clone` de tu propio
repo privado, etc.) y entrá a la carpeta:

```bash
cd ide-escm
cp .env.example .env
nano .env   # completar contraseñas seguras (NUNCA dejar las de ejemplo)
```

## 4. Levantar todo el stack

```bash
docker compose up -d
docker compose ps    # verificar que todos los servicios estén "healthy"/"running"
```

Primer arranque de GeoServer y GeoNetwork puede tardar 1-2 minutos.

## 5. Acceso a cada servicio

Reemplazá `IP_SERVIDOR` por la IP o dominio del servidor:

- GeoServer: `http://IP_SERVIDOR/geoserver/web` (usuario/clave definidos en `.env`)
- GeoNetwork: `http://IP_SERVIDOR/geonetwork`
- API Python: `http://IP_SERVIDOR/api/health`

## 6. Conectar GeoServer a PostGIS

Dentro de GeoServer (`Data > Stores > Add new Store > PostGIS`):

- Host: `postgis`  *(nombre del servicio Docker, no la IP)*
- Port: `5432`
- Database: el valor de `POSTGRES_DB` del `.env`
- User/Pass: los valores de `.env`

Desde ahí ya podés publicar cualquier tabla de `escm.capas_base` (o las que
crees) como capa WMS/WFS.

## 7. Publicar WMS/WFS

En `Layers > Add a new layer`, elegís el store de PostGIS y la tabla. GeoServer
genera automáticamente los endpoints estándar:

```
http://IP_SERVIDOR/geoserver/escm/wms
http://IP_SERVIDOR/geoserver/escm/wfs
```

Esto es lo que IDERA (u otro portal externo) va a consumir para "leer" los
mapas en tiempo real.

## 8. Metadatos ISO en GeoNetwork

Cada capa publicada en GeoServer debería tener su registro de metadatos en
GeoNetwork (autor, fecha, proyección, restricciones de acceso). GeoNetwork
trae plantillas ISO 19115/19139 listas para completar desde su interfaz web.

## 9. Red (además del servidor en sí)

Esto hay que pedirlo a IT/el proveedor cloud, no se resuelve con Docker:

- **IP pública fija**: imprescindible para que IDERA pueda cosechar el catálogo
  de GeoNetwork de forma confiable.
- **Dominio institucional**: mapear el nodo a un subdominio (ej.
  `ide.escm.undef.edu.ar`) apuntando a esa IP.
- **Ancho de banda**: simétrico, mínimo 100 Mbps (ideal 1 Gbps) para servir WMS/WFS
  con concurrencia razonable.
- **Puerto 22 (SSH)**: cerrado al público; solo accesible por VPN institucional o
  IPs en whitelist.

## 10. Seguridad y soberanía de datos

Puntos clave para un entorno institucional/militar:

- **Firewall**: usar `ufw` y exponer a Internet solo el puerto 80/443 (Nginx).
  PostGIS (5432) y los puertos internos de GeoServer/GeoNetwork **no** deberían
  quedar expuestos directamente — ya están aislados en la red interna de Docker.

  ```bash
  sudo ufw allow OpenSSH
  sudo ufw allow 80/tcp
  sudo ufw allow 443/tcp
  sudo ufw enable
  ```

- **HTTPS**: agregar Certbot (Let's Encrypt) delante de Nginx, o terminar SSL
  en un balanceador si el servidor está detrás de uno.

- **Capas restringidas/militares**: GeoServer permite reglas de seguridad por
  capa/workspace (`Security > Layers`) para exigir login en capas sensibles.
  La columna `clasificacion` en `escm.capas_base` está pensada para que la API
  en Python filtre además a nivel de aplicación antes de servir cualquier dato
  restringido.

- **Backups**: el volumen `postgis_data` contiene toda la información crítica.
  Programar `pg_dump` periódico y copiarlo fuera del servidor.

  ```bash
  docker exec ide_postgis pg_dump -U ide_admin ide_escm > backup_$(date +%F).sql
  ```

- **Actualizaciones**: mantener las imágenes de Docker actualizadas
  (`docker compose pull && docker compose up -d`) para parches de seguridad.

## 11. Apagar / reiniciar

```bash
docker compose down          # detiene todo, conserva los volúmenes (datos)
docker compose down -v       # ¡BORRA también los datos! usar con cuidado
docker compose restart geoserver
```

---

## Notas sobre la capa Python (API)

`api/main.py` es un punto de partida con FastAPI. Ahí es donde conviene ir
agregando:

- Autenticación (JWT/OAuth2) para capas restringidas y militares.
- Endpoints a medida para IDERA u otros consumidores institucionales.
- Automatización de publicación en GeoServer vía su REST API
  (`http://geoserver:8080/geoserver/rest`) en lugar de hacerlo a mano.
- Validaciones propias antes de insertar geometrías en PostGIS.
