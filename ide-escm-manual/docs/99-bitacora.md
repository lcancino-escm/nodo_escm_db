[⬅ Índice](../README.md) · [◀ Último capítulo existente](03-dimensionamiento.md)

# Bitácora de avances

Registro cronológico de avances del proyecto. **Se agrega arriba de todo**
— no se reescribe lo viejo. Ver el formato en
[CONTRIBUTING.md](../CONTRIBUTING.md).

---

## 11/07/2026 — Leonardo (con Claude)

- Arquitectura Docker completa: PostGIS, GeoServer, GeoNetwork, API en
  FastAPI y Nginx como proxy, con dimensionamiento de RAM/CPU para el
  escenario MVP (4 vCPU / 8 GB).
- Esquema `escm.investigaciones` migrado y ampliado con los campos reales
  del repositorio (DSpace): palabras clave, editorial, citación,
  descripción, colección.
- Migración del prototipo original (`tesis.db`, 3 registros) a PostGIS.
- Cargador masivo de fichas del repositorio (`cargar_tesis_dspace.py`),
  idempotente por URI, listo para las 172 tesinas.
- Manual técnico-funcional en Word (versión institucional).
- Este manual en GitHub, capítulo por capítulo.
- Reconstrucción de la historia completa del proyecto a partir del
  historial de Google AI Studio (ver [capítulo 0](00-historia-del-proyecto.md))
  y cronograma de horas (`Planning_IDE-ESCM.xlsx`).
- **Próximo paso:** cargar las 172 tesinas reales (Leonardo va pegando
  las fichas en `data/tesis_dspace.txt`), autenticación de capas
  restringidas, HTTPS + dominio institucional.

## 27/05/2026 — Leonardo (Google AI Studio)

- Redacción del documento técnico de requerimientos para la Secretaría
  de Extensión y Vinculación Universitaria, aplicando la metodología de
  *Buenas Prácticas en la Dirección y Gestión de Proyectos Informáticos*
  (Maigua y López, UTN, 2012).
- Recopilación de bibliografía sobre creación y administración de una IDE.

## 21/05/2026 — Leonardo (Google AI Studio)

- Debug del visualizador estático: error de red al hacer `fetch` de
  `tesis.db` en `localhost`, diagnóstico de la causa (seguridad del
  navegador, no error de código).
- Primeras pruebas de migración de la estructura de base de datos plana
  hacia GitHub para que se vea desde el navegador.

## 29–30/04/2026 — Leonardo (Google AI Studio)

- Troubleshooting en QGIS: falla en la composición de Atlas (vistas
  gráficas) y representación incompleta de polígonos. Actividad docente/
  operativa en paralelo al desarrollo del nodo.

## 18/04/2026 — Leonardo (Google AI Studio)

- Migración de la conversación de proyecto a otra cuenta de Google
  (administrativo).

## 15–16/04/2026 — Leonardo (Google AI Studio)

- Definición de la hoja de ruta con tres herramientas de IA (NotebookLM,
  AI Studio, Project IDX) para dividir el trabajo del proyecto.
- Primer diseño de la arquitectura profesional: Docker Compose con
  PostgreSQL+PostGIS, GeoServer (WMS/WFS) y Nginx con SSL — la base de lo
  que hoy es el [capítulo 2](02-arquitectura.md) de este manual.

## 23–24/03/2026 — Leonardo (Google AI Studio)

- Arranque del proyecto IDE-ESCM: primera versión de `index.html`.
- Primera estructura de datos en SQLite (organizada por año) para
  mostrar las tesis en un visualizador dentro del navegador — el origen
  de `tesis.db` y de la tabla `investigaciones`.

## 28/02–02/03/2026 — Leonardo (Google AI Studio)

- Cierre del armado del puesto de trabajo (hardware) que se usaría para
  el desarrollo del proyecto (GIS, CAD, procesamiento de imágenes
  satelitales, Docker, clases en vivo).

---
[⬅ Índice](../README.md) · [◀ Último capítulo existente](03-dimensionamiento.md)
