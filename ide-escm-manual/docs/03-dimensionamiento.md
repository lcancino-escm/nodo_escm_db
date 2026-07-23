[⬅ Índice](../README.md) · [◀ Anterior](02-arquitectura.md) · [Siguiente ▶](04-modelo-de-datos.md)

# 3. Dimensionamiento de hardware

_Última actualización: 10/07/2026_

Perfil de carga de una IDE universitaria: tráfico bajo a moderado, picos
de CPU cuando GeoServer renderiza mapas complejos on-the-fly, y una
demanda de lectura/escritura crítica en PostGIS (requiere disco rápido,
SSD/NVMe — no HDD mecánico).

## Escenario MVP (servidor base de producción)

| Recurso | Especificación |
|---|---|
| CPU | 4 vCPU |
| RAM | 8 GB |
| Almacenamiento | 100 GB SSD/NVMe |
| Sistema operativo | Ubuntu Server 22.04 LTS o 24.04 LTS, sin interfaz gráfica |
| Red | IP pública fija + dominio institucional + ≥100 Mbps simétricos |

## Escenario "soporte institucional" (objetivo a 1 año)

Cuando el nodo sea cosechado por IDERA y se empiecen a subir imágenes
satelitales (rasters pesados):

- 8 vCPU
- 16–32 GB RAM (GeoServer escala fuerte con rasters y estilos complejos)
- 200 GB SSD/NVMe + almacenamiento en frío opcional (HDD o S3) para
  series históricas de imágenes satelitales

## Distribución de RAM entre contenedores (escenario MVP)

| Servicio | RAM asignada | Justificación |
|---|---|---|
| PostGIS | 2 GB | `shared_buffers`/`effective_cache_size` tuneados |
| GeoServer | 3 GB | Heap JVM 2.5 GB + margen para caché de teselas |
| GeoNetwork | 1 GB | Tomcat + catálogo de metadatos |
| API (Python) | 256 MB | FastAPI, uso liviano |
| Nginx | 128 MB | Proxy reverso |
| **Total** | **~6.4 GB** | Deja margen para el SO en un host de 8 GB |

Estos valores están fijados en `docker-compose.yml` con `mem_limit` y
`cpus` por servicio. Si el servidor real termina siendo el escenario
institucional (16–32 GB), conviene subir `MAXIMUM_MEMORY` de GeoServer y
`shared_buffers` de PostGIS proporcionalmente — son los dos que más se
benefician de RAM extra.

## Pitch para pedir el servidor

> "Para la primera etapa operativa del Nodo IDE-ESCM, que soportará la
> infraestructura base y la carga de tesinas vectoriales bajo estándares
> IDERA, requerimos un servidor Linux virtualizado con 4 núcleos de
> procesamiento, 8 GB de memoria RAM y un disco de estado sólido (SSD) de
> 100 GB, garantizando una IP pública fija. Esta arquitectura mínima es
> escalable a futuro."

---
[⬅ Índice](../README.md) · [◀ Anterior](02-arquitectura.md) · [Siguiente ▶](04-modelo-de-datos.md)
