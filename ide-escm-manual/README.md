# Manual Técnico-Funcional — Nodo IDE-ESCM

Documentación viva del desarrollo del nodo de Infraestructura de Datos
Espaciales de la Escuela de Ciencias del Mar (IDE-ESCM). Se actualiza a
medida que avanza el proyecto — cada tema nuevo es un capítulo aparte
dentro de `docs/`.

> **Equipo:** este manual lo mantienen conjuntamente Leonardo (Buenos
> Aires) y su compañero de proyecto (Salta). Ver [CONTRIBUTING.md](CONTRIBUTING.md)
> antes de editar, para evitar pisarse el trabajo.

## Índice

| # | Capítulo | Estado |
|---|----------|--------|
| 0 | [Historia del proyecto](docs/00-historia-del-proyecto.md) | ✅ |
| 1 | [Introducción y alcance](docs/01-introduccion.md) | ✅ |
| 2 | [Arquitectura general](docs/02-arquitectura.md) | ✅ |
| 3 | [Dimensionamiento de hardware](docs/03-dimensionamiento.md) | ✅ |
| 4 | [Modelo de datos](docs/04-modelo-de-datos.md) | ⬜ pendiente |
| 5 | [Estructura del proyecto](docs/05-estructura-proyecto.md) | ⬜ pendiente |
| 6 | [Despliegue en el servidor](docs/06-despliegue.md) | ⬜ pendiente |
| 7 | [Migración del prototipo SQLite](docs/07-migracion-sqlite.md) | ⬜ pendiente |
| 8 | [Carga masiva de tesinas (DSpace)](docs/08-carga-tesis-dspace.md) | ⬜ pendiente |
| 9 | [API de orquestación](docs/09-api.md) | ⬜ pendiente |
| 10 | [Seguridad y red](docs/10-seguridad-red.md) | ⬜ pendiente |
| 11 | [Autenticación de capas restringidas](docs/11-autenticacion.md) | ⬜ pendiente |
| 12 | [HTTPS y dominio institucional](docs/12-https-dominio.md) | ⬜ pendiente |
| — | [Bitácora de avances](docs/99-bitacora.md) | ✅ (poblada con historial real) |

**Leyenda:** ✅ documentado y funcionando · 🟡 en progreso · ⬜ pendiente de iniciar · 🔄 se actualiza en cada avance

## Planning y horas del proyecto

`Planning_IDE-ESCM.xlsx` (fuera de este repo de documentación, se
distribuye junto con los entregables de gestión) trae el cronograma real
del proyecto: detalle de sesiones con fecha/hora, resumen de horas por
semana, y un Gantt semanal por fase — reconstruido a partir de los
timestamps reales del historial de trabajo, no estimado.

## Cómo leer este manual

Está pensado para leerse directo en GitHub, sin instalar nada: entrás a
la carpeta `docs/`, abrís el capítulo que te interese, y los enlaces
entre capítulos funcionan solos (son links relativos dentro del repo).

## Cómo agregar un capítulo nuevo

Ver la guía completa en [CONTRIBUTING.md](CONTRIBUTING.md). En resumen:

1. Crear `docs/NN-titulo-corto.md` (siguiente número disponible).
2. Agregar la fila correspondiente en la tabla de arriba.
3. Registrar el avance en [docs/99-bitacora.md](docs/99-bitacora.md).
4. Commit y push.

## Proyecto de código

El código del stack (Docker Compose, API, scripts de carga) vive en el
repositorio del proyecto `ide-escm/` — este manual documenta el *por qué*
y el *cómo* de cada parte; el código en sí es la fuente de verdad de la
implementación exacta.
