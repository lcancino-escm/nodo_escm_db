[⬅ Índice](../README.md) · [◀ Anterior](00-historia-del-proyecto.md) · [Siguiente ▶](02-arquitectura.md)

# 1. Introducción y alcance

_Última actualización: 10/07/2026_

## Objetivo del nodo

El nodo IDE-ESCM (Infraestructura de Datos Espaciales de la Escuela de
Ciencias del Mar) tiene como objetivo publicar los geoservicios y
metadatos de las tesinas de la Licenciatura en Cartografía bajo
estándares OGC (WMS/WFS) e ISO (19115/19139), de forma compatible con la
cosecha de metadatos de **IDERA** (Infraestructura de Datos Espaciales de
la República Argentina).

## Por qué un servidor propio (y no archivos sueltos)

- **Geoservicios en tiempo real**: para que IDERA "lea" los mapas, los
  datos no pueden estar en un `.zip` o `.txt` — se transmiten por WMS
  (imágenes) y WFS (vectores) desde un servidor corriendo 24/7
  (GeoServer).
- **Base de datos espacial**: a nivel institucional, con múltiples
  usuarios consultando o cargando mapas a la vez, hace falta un motor
  relacional geográfico (PostgreSQL + PostGIS), no un archivo SQLite.
- **Catálogo de metadatos**: IDERA exige que cada dato tenga su "DNI"
  (autor, fecha, proyección) bajo norma ISO — eso lo resuelve GeoNetwork.
- **Soberanía y seguridad**: un servidor propio da control total sobre
  qué datos son públicos y cuáles restringidos/militares, sin depender de
  servicios externos.

## Alcance de esta etapa

Estamos en la etapa de **prototipo funcional / MVP**. Ya está resuelto:

- Arquitectura completa en Docker (PostGIS, GeoServer, GeoNetwork, API
  propia, proxy).
- Modelo de datos para el catálogo de tesinas.
- Migración del prototipo original en SQLite.
- Carga masiva de fichas del repositorio institucional.

Queda para etapas siguientes: autenticación real de capas
restringidas/militares, HTTPS con dominio institucional, y la carga
completa de las 172 tesinas. El estado detallado, capítulo por capítulo,
está en el [índice](../README.md).

---
[⬅ Índice](../README.md) · [◀ Anterior](00-historia-del-proyecto.md) · [Siguiente ▶](02-arquitectura.md)
