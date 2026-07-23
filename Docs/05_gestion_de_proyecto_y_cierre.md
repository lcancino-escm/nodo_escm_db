# Documentación de gestión de proyecto y mensajes finales

_Chunks originales 275–284 del export de Google AI Studio._

---


### [276] 🧑 Leonardo

actualizar  esta documentacion para el proyecto


### [278] 🤖 Gemini

Leonardo, he recibido y procesado las 238 páginas del libro **"Buenas Prácticas en la Dirección y Gestión de Proyectos Informáticos"** (Maigua y López, UTN, 2012). 

Como tu **Ingeniero y Project Manager**, entiendo exactamente lo que necesitas. No vamos a hacer un resumen teórico del libro; vamos a **APLICAR** su metodología directamente a nuestro proyecto para generar la documentación formal que te exigirán las Secretarías en la reunión del 28 de mayo.

A continuación, he redactado la **Documentación Gerencial del Proyecto IDE ESCM**, estructurada según los estándares del libro que me compartiste (PMI / IEEE 830), pero con los datos reales de tu infraestructura actual (i7-14700, RTX 5070 Ti, Docker, SQLite, IDERA).

Copia este texto y guárdalo en un archivo de Word. Es tu **Master Plan**.

---

# 📑 PLAN DE DIRECCIÓN Y GESTIÓN DE PROYECTO (PDP)
**PROYECTO:** Implementación de Nodo Universitario IDE ESCM
**MARCO METODOLÓGICO:** Basado en "Buenas Prácticas en Dirección de Proyectos Informáticos" (UTN) y estándares OGC/IDERA.

## 1. ACTA DE CONSTITUCIÓN DEL PROYECTO (Ref. Libro Cap. 3.3.2)

*   **Nombre del Proyecto:** Nodo Universitario IDE ESCM.
*   **Organización Patrocinadora:** Secretaría de Extensión y Vinculación Universitaria (SEU) / FadARA.
*   **Director del Proyecto (Project Manager):** Prof. Lic. Leonardo Cancino.
*   **Necesidad del Negocio:** Integrar a la ESCM a la red nacional IDERA, garantizando la soberanía tecnológica y de datos, visibilizando la producción científica (tesis/investigaciones) y modernizando la currícula de la Licenciatura en Cartografía mediante el uso de estándares OGC (WMS/WFS).
*   **Infraestructura Asignada (Recursos Físicos):** Workstation de Alto Rendimiento (Intel Core i7-14700, 32GB RAM DDR5, GPU NVIDIA RTX 5070 Ti 16GB, PSU ASUS TUF 1000W).

## 2. ESTRUCTURA DE RECURSOS HUMANOS (Ref. Libro Cap. 6)

Según la clasificación de perfiles del proyecto informático, el equipo se estructura de la siguiente manera:

*   **Director del Proyecto / Arquitecto de Sistemas:** Lic. Leonardo Cancino. (Responsable de la infraestructura de servidores, base de datos PostGIS/SQLite, despliegue en Docker y código fuente del visor web).
*   **Codirector / Analista Funcional:** Tec. Esp. Diego Carcasson. (Apoyo en la validación de requisitos y flujos de trabajo institucionales).
*   **Especialista Temático (SME):** Lic. Flavia Di Biase. (Asesoramiento en la normalización de datos oceanográficos y de mareas).
*   **Equipo de Desarrollo (Operadores/Data Entry):** Alumnos de la Lic. en Cartografía. (Encargados de limpiar fuentes de datos, estilización con archivos SLD y redacción de metadatos ISO 19115).

## 3. GESTIÓN DE RIESGOS (Ref. Libro Cap. 5)

Identificación y planes de contingencia para asegurar el éxito del Nodo IDE:

| ID | Riesgo Identificado | Impacto | Probabilidad | Estrategia de Respuesta (Mitigación) |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | **Cuello de botella en Hardware (RAM)**: El sistema actual posee RAM en *Single Channel*, lo que puede colapsar el renderizado en QGIS al procesar el Atlas. | ALTO | ALTA | **Mitigación (Software):** Limitar los hilos de CPU en QGIS a 16 y forzar aceleración por GPU OpenCL. **Solución (Hardware):** Adquisición programada de un 2do módulo de 32GB DDR5. |
| **R2** | **Obsolescencia de Plataforma Cloud**: Cierre anunciado de Firebase Studio por parte de Google. | ALTO | MEDIA | **Evitar:** Migrar el entorno de desarrollo a local (VS Code + Node.js) asegurando soberanía del código, usando Firebase solo como Hosting. |
| **R3** | **Incumplimiento Normativo IDERA**: Que el visor web no cumpla con los estándares de interoperabilidad nacional. | CRÍTICO | BAJA | **Control:** Auditoría estricta de requerimientos mediante IA (NotebookLM) sobre documentos oficiales de IDERA. Implementación obligatoria de GeoNetwork para perfil LAMP. |

## 4. CICLO DE VIDA Y FASES DEL PROYECTO (Ref. Libro Cap. 2 y 4)

El proyecto adopta un **Modelo Iterativo e Incremental** (Ver Fig. 33 del libro), dividido en las siguientes fases operativas:

### FASE 1: Planeación y Prototipado (Completada)
*   **Hito:** Despliegue del Prototipo V2 estático en GitHub Pages (`nodo_escm_db`).
*   **Entregable:** Interfaz Web con Modo Lector, motor de base de datos integrado en navegador (SQLite WASM) y geocodificación de 35 tesis de prueba.

### FASE 2: Ejecución Backend y Dockerización (En progreso - Marzo/Abril)
*   **Hito:** Puesta en marcha de la arquitectura "Server-side".
*   **Entregables:** 
    *   Contenedor Docker con **PostgreSQL + PostGIS** (Migración de datos de SQLite a PostGIS).
    *   Contenedor Docker con **GeoServer** para la emisión de estándares OGC (WMS/WFS).

### FASE 3: Estandarización y Metadatos (Mayo/Junio)
*   **Hito:** Cumplimiento total de la norma IDERA.
*   **Entregables:**
    *   Diseño y aplicación de archivos **SLD** para simbología de mapas.
    *   Implementación de **GeoNetwork** para la redacción del catálogo de metadatos ISO 19115.

### FASE 4: Mantenimiento e Implantación Institucional (Julio en adelante)
*   **Hito:** Paso a producción y capacitación.
*   **Entregables:**
    *   Migración del ecosistema Docker de la Workstation local a los servidores cloud de la institución (Oracle / Armada).
    *   Elaboración de **Manuales de Usuario** y talleres prácticos para que los alumnos de Cartografía asuman la carga de nuevas tesis.

## 5. COMUNICACIÓN Y GESTIÓN DE INTERESADOS (Ref. Libro Cap. 6.4.3)
*   **Stakeholders Clave:** Secretarías Académicas e Investigación.
*   **Hito de Comunicación:** Reunión del Jueves 28/05. 
*   **Estrategia:** Presentar el Prototipo V2 funcional, demostrando la no-dependencia de software privativo (ahorro de licencias Esri) y el posicionamiento de la ESCM como ente generador de información interoperable nacional.

---

### 👨‍💻 Comentario del Ingeniero (Off the record):

Leonardo, el libro que pasaste es excelente para sentar bases metodológicas. Lo que he hecho arriba es **traducir la teoría académica de ese libro a la realidad tecnológica de tu proyecto**. 

Si presentas este documento a las autoridades, verán a un **Director de Proyectos** que tiene todo bajo absoluto control técnico, financiero y de riesgos. 

¿Quieres que iniciemos la **Fase 2** e instalemos las herramientas en tu PC para empezar a programar el backend real con Docker?


### [281] 🧑 Leonardo

Esta es la bibliografia correspondiente a la creacion y administracion t gestion de una IDE


### [282] 🧑 Leonardo

hola


### [284] 🧑 Leonardo

tienes los datos de user del servidor que instale?
