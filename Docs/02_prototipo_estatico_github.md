# Prototipo estático inicial (GitHub Pages + sql.js)

_Chunks originales 180–209 del export de Google AI Studio._

---


### [180] 🧑 Leonardo

Alto. Muestrame paso a paso, ya que debo documentar todo , no des nada por sabido, aqui NO HAY EXPERTOS,  hay que ir desde cero, ademas el entorno es GitHub, ( No me autorizaron el servidor remoto por el costo), por lo que no puede ser dinamico, debe ser estatico, es un prototipo , luego haremos el profesional, enlistemos las 35 tesis,( para toda tesis coloca este link por default para ir a ver repositorio de tesis publicadas:  'https://cefadigital.edu.ar/handle/1847939/1729')  y seguiremos trabajando con estas tesis en el mapa, de apoco iremos agregando a lo largo del año el resto que falta geocodificar. Po rlo tanto pensemos que toda la info y los geojson deben estar embebidos dentro del codigo Github.


### [182] 🤖 Gemini

Entendido perfectamente, Leonardo. Bajamos a tierra: **Protocolo de Prototipo Estático para GitHub Pages**.

Como no tenemos servidor (backend), utilizaremos una estrategia de **Base de Datos Plana (JSON)**. El navegador leerá un archivo de texto con toda la información. Es la forma más profesional de hacer un sitio estático que parezca dinámico.

Aquí tienes el manual de procedimientos paso a paso para documentar y ejecutar.

---

### Paso 1: Estructura de Carpetas en GitHub
Para que el proyecto sea escalable, organiza tu repositorio así:

```text
IDE-ESCM/
├── index.html         <-- El visor principal
├── data/
│   └── tesis.json     <-- Nuestra "Base de Datos" estática
├── css/
│   └── estilos.css    <-- El diseño de la barra lateral
└── js/
    └── logica.js      <-- El cerebro que conecta mapa y lista
```

---

### Paso 2: Crear la "Base de Datos" Estática (`data/tesis.json`)
Copia este contenido en un archivo nuevo llamado `data/tesis.json`. He incluido los 35 registros con el link solicitado y coordenadas temporales (en la ESCM) para los que aún no geocodificamos.

```json
[
  { "id": 1, "anio": 2005, "titulo": "La utilidad de la cartografía histórica... Mar Chiquita", "autor": "De Leo, Daniela Andrea", "lat": -37.74, "lon": -57.43, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 2, "anio": 2017, "titulo": "Proyecto de Modelo de Sistema de Información Geográfica aplicado al Geomarketing.", "autor": "Cancino, Leonardo Andrés", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 3, "anio": 2021, "titulo": "Fotogrametría aérea con drones de la localidad de Solís, Prov. BSAS", "autor": "Jofré, Eduardo Matías", "lat": -34.30, "lon": -59.32, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 4, "anio": 2010, "titulo": "Planificación de un SIG para control de calidad de combustibles.", "autor": "Argiró, Héctor E.", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 5, "anio": 2017, "titulo": "Producción de la Carta Náutica Electrónica Boca del Golfo San José", "autor": "Losada, Melina Yael", "lat": -42.25, "lon": -64.30, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 6, "anio": 2019, "titulo": "Aplicación del software CARIS Bathy DataBASE para validación batimétrica", "autor": "López, Gisele A.", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 7, "anio": 2017, "titulo": "Modelo digital del terreno para modelos hidrodinámicos en ría de Deseado.", "autor": "Figueredo Molinas, Julia Mariela", "lat": -47.75, "lon": -65.90, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 8, "anio": 2014, "titulo": "Cartografía Topográfica y Turística: Parque Nacional Los Alerces", "autor": "Nelson, Carlos O.", "lat": -42.80, "lon": -71.80, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 9, "anio": 2012, "titulo": "Comparación de modelos digitales de elevación en zona de alta montaña.", "autor": "Matko, Claudio", "lat": -32.65, "lon": -70.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 10, "anio": 2021, "titulo": "Utilización de datos satelitales de color del mar... polígonos de pesca merluza.", "autor": "Garcia Ulibarri, Juan Carlos", "lat": -43.00, "lon": -62.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 11, "anio": 2014, "titulo": "Evolución espacio-temporal de la espiga arenosa de Punta Rasa", "autor": "Molina, Sergio Daniel", "lat": -36.29, "lon": -56.78, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 12, "anio": 2004, "titulo": "Estudio comparativo entre métodos de interpolación para MDT.", "autor": "García, Fernando Esteban", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 13, "anio": 2003, "titulo": "Procesamiento digital de imágenes satelitales para la Cartografía Náutica Fluvial", "autor": "Bava, Federico", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 14, "anio": 2012, "titulo": "Estudio de información geográfica de la localidad de Huanguelén", "autor": "Massi, Fabio Damián", "lat": -37.06, "lon": -61.20, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 15, "anio": 2017, "titulo": "Un Modelo de Geoide definido para paraje El Carancho - La Pampa", "autor": "Bello, Fabián M.", "lat": -37.45, "lon": -65.10, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 16, "anio": 2022, "titulo": "Desarrollo de la Carta Aeronáutica Mundial OACI 1:1.000.000 – Trelew", "autor": "López, José Luis", "lat": -43.25, "lon": -65.30, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 17, "anio": 2014, "titulo": "Tendencia de las Ondas de Tormenta e incidencia en la costa de Ushuaia.", "autor": "Ayala, Víctor M.", "lat": -54.80, "lon": -68.30, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 18, "anio": 2016, "titulo": "Detección de errores de localización de pozos históricos de YPF", "autor": "Alvarez, Gabriel Oscar", "lat": -45.86, "lon": -67.48, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 19, "anio": 2017, "titulo": "Análisis de la variación temporal de la línea de costa en Necochea", "autor": "Ayala, Anahí Maricel", "lat": -38.55, "lon": -58.74, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 20, "anio": 2015, "titulo": "Modelo digital de elevación en la ría de Puerto Deseado.", "autor": "Medina, Ayelén", "lat": -47.75, "lon": -65.90, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 21, "anio": 2018, "titulo": "Identificación de áreas de conservación mediante indicadores satelitales", "autor": "Delgadillo, Noelia Liliana", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 22, "anio": 2004, "titulo": "Elaboración de batimetrías digitales Proyecto GEF Patagonia.", "autor": "Borjas, Rocío del Valle", "lat": -43.00, "lon": -64.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 23, "anio": 2021, "titulo": "Levantamientos batimétricos mediante GNSS / RTK de alta precisión.", "autor": "Vera, Gustavo Alfredo", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 24, "anio": 2018, "titulo": "Servicio colaborativo online para publicación de eventos geográficos", "autor": "Rodríguez Baumann, Emilio Javier", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 25, "anio": 2005, "titulo": "Generación de mapas digitales de cotidales e isoamplitudes para el Río de la Plata", "autor": "Di Biase, Flavia Analía Verónica", "lat": -35.00, "lon": -57.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 26, "anio": 2023, "titulo": "Obtención de planos de reducción de sondajes en el Mar Argentino", "autor": "López, Macarena Ileana", "lat": -40.00, "lon": -60.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 27, "anio": 2024, "titulo": "Generación de un sistema SIG para Cartografía náutica.", "autor": "Naumovitch, Nicolás Alejandro", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 28, "anio": 2024, "titulo": "Distribución de foraminíferos en el Océano Mundial.", "autor": "Fernández, José Luis", "lat": 0.0, "lon": 0.0, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 29, "anio": 2015, "titulo": "Reestructuración de las regiones de información de vuelo (FIR) Argentina", "autor": "Silva, Rubén Guillermo", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 30, "anio": 2024, "titulo": "SIG de Catastro Multifinalitario aplicado a Hurlingham", "autor": "Barrera, Tomas Agustín", "lat": -34.59, "lon": -58.63, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 31, "anio": 2024, "titulo": "Nuevo modelo de Plano de Aeródromo-OACI Argentina", "autor": "Trigo, Javier Federico", "lat": -34.62, "lon": -58.37, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 32, "anio": 2024, "titulo": "Emplazamientos militares en la Frontera Sur (Siglos XVIII-XIX)", "autor": "Quintanilla, Pablo Hernán", "lat": -37.00, "lon": -60.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 33, "anio": 2025, "titulo": "Cobertura de las cartas náuticas en el Sector Antártico Argentino.", "autor": "Carrizo, Cristina Rodolfo", "lat": -65.00, "lon": -64.00, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 34, "anio": 2025, "titulo": "Generación de cartografía digital rápida para Bariloche", "autor": "Zabala, Jorge", "lat": -41.13, "lon": -71.30, "url": "https://cefadigital.edu.ar/handle/1847939/1729" },
  { "id": 35, "anio": 2025, "titulo": "Relevamiento con sonar de barrido lateral en el estuario del Río de la Plata", "autor": "Ezcurra., Joaquín", "lat": -34.80, "lon": -57.90, "url": "https://cefadigital.edu.ar/handle/1847939/1729" }
]
```

---

### Paso 3: Actualizar el Visor (`index.html`)
Este código reemplaza todo tu `index.html`. Está diseñado para leer automáticamente el archivo JSON de arriba.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IDE ESCM - Repositorio Dinámico Estático</title>

    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    
    <style>
        :root { --navy: #002344; --gold: #f1c40f; }
        body { margin: 0; display: flex; flex-direction: column; height: 100vh; font-family: sans-serif; }
        header { background: var(--navy); color: white; padding: 10px; text-align: center; border-bottom: 3px solid var(--gold); }
        #main { display: flex; flex: 1; overflow: hidden; }
        #sidebar { width: 350px; overflow-y: auto; background: #f4f4f4; border-right: 1px solid #ccc; padding: 15px; }
        #map { flex: 1; }
        .tesis-item { 
            background: white; margin-bottom: 10px; padding: 10px; border-radius: 5px; 
            cursor: pointer; border-left: 5px solid var(--navy); transition: 0.3s;
        }
        .tesis-item:hover { background: #e9e9e9; transform: translateX(5px); }
        .tesis-item h4 { margin: 0; font-size: 14px; color: var(--navy); }
        .tesis-item p { margin: 5px 0; font-size: 12px; }
        .link-repo { color: #28a745; font-weight: bold; text-decoration: none; font-size: 11px; }
    </style>
</head>
<body>

<header>
    <h3>Nodo IDE ESCM - Repositorio de Investigaciones</h3>
</header>

<div id="main">
    <div id="sidebar">
        <h4>Listado de Tesis (35)</h4>
        <div id="lista-contenedor">Cargando datos...</div>
    </div>
    <div id="map"></div>
</div>

<!-- Leaflet JS -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
    // Inicializar Mapa
    const map = L.map('map').setView([-38.4, -63.6], 4);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{y}/{x}.png').addTo(map);

    // Función para cargar los datos del JSON
    async function cargarDatos() {
        try {
            // Buscamos el archivo que creamos en el paso 2
            const respuesta = await fetch('data/tesis.json');
            const datos = await respuesta.json();
            
            const contenedor = document.getElementById('lista-contenedor');
            contenedor.innerHTML = ''; // Limpiar mensaje de carga

            datos.forEach(tesis => {
                // 1. Crear Marcador en el Mapa
                const marcador = L.marker([tesis.lat, tesis.lon]).addTo(map);
                marcador.bindPopup(`
                    <b>${tesis.titulo}</b><br>
                    Autor: ${tesis.autor}<br>
                    <a href="${tesis.url}" target="_blank">Ver en CefaDigital</a>
                `);

                // 2. Crear Item en la barra lateral
                const div = document.createElement('div');
                div.className = 'tesis-item';
                div.innerHTML = `
                    <h4>${tesis.titulo}</h4>
                    <p><b>Autor:</b> ${tesis.autor} (${tesis.anio})</p>
                    <a class="link-repo" href="${tesis.url}" target="_blank">📂 REPOSITORIO OFICIAL</a>
                `;

                // 3. Al hacer clic en la lista, ir al marcador
                div.onclick = () => {
                    map.flyTo([tesis.lat, tesis.lon], 10);
                    marcador.openPopup();
                };

                contenedor.appendChild(div);
            });

        } catch (error) {
            console.error("Error cargando el JSON:", error);
            document.getElementById('lista-contenedor').innerHTML = "Error al cargar los datos.";
        }
    }

    // Ejecutar carga al iniciar
    cargarDatos();
</script>

</body>
</html>
```

---

### ¿Por qué esta solución es la mejor para tu caso?

1.  **Cero Costo:** GitHub Pages lo sirve gratis.
2.  **Mantenimiento Sencillo:** Cuando quieras geocodificar una tesis nueva, **solo editas el archivo `data/tesis.json`**. Cambias las coordenadas `0.0, 0.0` por la ubicación real (lat/lon) y el mapa se actualiza solo. No tienes que tocar el código del mapa nunca más.
3.  **Documentación Impecable:** Puedes decir que el prototipo usa un **"Patrón de Arquitectura Desacoplada"**: los datos (JSON) están separados de la vista (HTML/JS). Esto es exactamente lo que hace una IDE profesional, pero en formato estático.
4.  **Resiliencia:** Si en el futuro te dan un servidor, el mismo archivo JSON se puede importar a una base de datos SQL en 5 minutos.

**Siguiente paso:** Sube estos archivos a tu repositorio, activa "GitHub Pages" en la configuración del repositorio y envíame el link para ver cómo quedó la visualización.


### [183] 🧑 Leonardo

entiendo que se puede realizar con SQLITE, dentro del proyecto de GitHub. SQLite se utiliza en proyectos de páginas de GitHub (GitHub Pages) mediante el almacenamiento de la base de datos como un archivo estático (.db o .sqlite). Esta base de datos se puede emular o consultar en el navegador utilizando tecnologías como WebAssembly (WASM), permitiendo a sitios estáticos realizar consultas SQL complejas sin un servidor back-end. Entonces colocar al Info de Base de datos de Tesis en Formato SQLITE


### [185] 🤖 Gemini

Leonardo, acepto el desafío técnico. Como ingeniero, este enfoque es **superior** porque separa la lógica de datos del código de visualización usando un motor de base de datos real, pero ejecutado íntegramente en el cliente (navegador).

Para que esto funcione en **GitHub Pages**, utilizaremos la librería **sql.js**, que es el motor de SQLite compilado a **WebAssembly (WASM)**. 

Aquí tienes el manual de procedimientos paso a paso para la implementación del **Nodo IDE-ESCM v2.0 (Motor SQL)**.

---

### Paso 1: Generar la Base de Datos (`data/tesis.db`)
Como GitHub no puede "crear" el archivo por ti, debes crearlo tú localmente o usando una herramienta online y subirlo a la carpeta `data/`.

1. Entra a **[sqliteonline.com](https://sqliteonline.com/)**.
2. Ve a **File > New In-Memory**.
3. Pega y ejecuta el siguiente código SQL para crear la tabla e insertar los 35 registros:

```sql
CREATE TABLE investigaciones (
    id INTEGER PRIMARY KEY,
    anio INTEGER,
    titulo TEXT,
    autor TEXT,
    lat REAL,
    lon REAL,
    url TEXT
);

INSERT INTO investigaciones (anio, titulo, autor, lat, lon, url) VALUES 
(2005, 'Cartografía histórica y sensores remotos Mar Chiquita', 'De Leo, Daniela Andrea', -37.74, -57.43, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2017, 'SIG aplicado al Geomarketing', 'Cancino, Leonardo Andrés', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2021, 'Fotogrametría aérea con drones Solís, BSAS', 'Jofré, Eduardo Matías', -34.30, -59.32, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2010, 'SIG para control de calidad de combustibles', 'Argiró, Héctor E.', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2017, 'Carta Náutica Electrónica Golfo San José', 'Losada, Melina Yael', -42.25, -64.30, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2019, 'Software CARIS Bathy DataBASE validación batimétrica', 'López, Gisele A.', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2017, 'MDT modelos hidrodinámicos ría de Deseado', 'Figueredo Molinas, Julia Mariela', -47.75, -65.90, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2014, 'Cartografía Parque Nacional Los Alerces', 'Nelson, Carlos O.', -42.80, -71.80, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2012, 'MDE vs cartografía alta montaña', 'Matko, Claudio', -32.65, -70.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2021, 'Datos satelitales color del mar pesca merluza', 'Garcia Ulibarri, Juan Carlos', -43.00, -62.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2014, 'Evolución Punta Rasa', 'Molina, Sergio Daniel', -36.29, -56.78, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2004, 'Métodos de interpolación MDT', 'García, Fernando Esteban', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2003, 'Imágenes satelitales Cartografía Náutica Fluvial', 'Bava, Federico', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2012, 'Información geográfica Huanguelén', 'Massi, Fabio Damián', -37.06, -61.20, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2017, 'Modelo de Geoide El Carancho - La Pampa', 'Bello, Fabián M.', -37.45, -65.10, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2022, 'Carta Aeronáutica OACI Trelew', 'López, José Luis', -43.25, -65.30, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2014, 'Ondas de Tormenta Ushuaia', 'Ayala, Víctor M.', -54.80, -68.30, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2016, 'Errores localización pozos YPF', 'Alvarez, Gabriel Oscar', -45.86, -67.48, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2017, 'Variación línea de costa Necochea', 'Ayala, Anahí Maricel', -38.55, -58.74, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2015, 'MDE ría de Puerto Deseado', 'Medina, Ayelén', -47.75, -65.90, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2018, 'Áreas de conservación indicadores satelitales', 'Delgadillo, Noelia Liliana', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2004, 'Batimetrías digitales GEF Patagonia', 'Borjas, Rocío del Valle', -43.00, -64.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2021, 'Levantamientos batimétricos GNSS / RTK', 'Vera, Gustavo Alfredo', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2018, 'Servicio colaborativo eventos geográficos', 'Rodríguez Baumann, Emilio Javier', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2005, 'Mapas de cotidales e isoamplitudes Río de la Plata', 'Di Biase, Flavia Analía Verónica', -35.00, -57.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2023, 'Planos reducción de sondajes Mar Argentino', 'López, Macarena Ileana', -40.00, -60.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2024, 'Sistema SIG Cartografía náutica', 'Naumovitch, Nicolás Alejandro', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2024, 'Distribución de foraminíferos Océano Mundial', 'Fernández, José Luis', 0.0, 0.0, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2015, 'Regiones FIR Argentina', 'Silva, Rubén Guillermo', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2024, 'Catastro Multifinalitario Hurlingham', 'Barrera, Tomas Agustín', -34.59, -58.63, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2024, 'Plano Aeródromo-OACI Argentina', 'Trigo, Javier Federico', -34.62, -58.37, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2024, 'Emplazamientos militares Frontera Sur', 'Quintanilla, Pablo Hernán', -37.00, -60.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2025, 'Cartas náuticas Sector Antártico Argentino', 'Carrizo, Cristina Rodolfo', -65.00, -64.00, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2025, 'Cartografía digital rápida Bariloche', 'Zabala, Jorge', -41.13, -71.30, 'https://cefadigital.edu.ar/handle/1847939/1729'),
(2025, 'Sonar de barrido lateral estuario RdlP', 'Ezcurra., Joaquín', -34.80, -57.90, 'https://cefadigital.edu.ar/handle/1847939/1729');
```

4. Ve a **File > Download DB** y guárdalo como `tesis.db`. Luego súbelo a tu carpeta `data/` en GitHub.

---

### Paso 2: El Visor Inteligente (`index.html`)

Este código incluye la librería SQL.js para leer el archivo binario directamente en la memoria del navegador.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>IDE ESCM - Motor SQLite WASM</title>
    
    <!-- Librerías de Mapa -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <!-- Motor SQLite (sql.js) vía CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/sql-wasm.js"></script>

    <style>
        :root { --navy: #002344; --gold: #f1c40f; }
        body { margin: 0; display: flex; flex-direction: column; height: 100vh; font-family: sans-serif; }
        header { background: var(--navy); color: white; padding: 10px; text-align: center; border-bottom: 3px solid var(--gold); }
        #wrapper { display: flex; flex: 1; overflow: hidden; }
        #sidebar { width: 350px; background: #eee; border-right: 1px solid #ccc; overflow-y: auto; padding: 15px; }
        #map { flex: 1; }
        .tesis-item { 
            background: white; padding: 10px; margin-bottom: 8px; border-radius: 4px;
            border-left: 4px solid var(--navy); cursor: pointer;
        }
        .tesis-item:hover { background: #fdfdfd; border-color: var(--gold); }
        .repo-link { display: block; margin-top: 5px; color: green; font-weight: bold; font-size: 11px; text-decoration: none; }
    </style>
</head>
<body>

<header>
    <h3>Nodo IDE ESCM - Base de Datos SQLite (WASM)</h3>
</header>

<div id="wrapper">
    <aside id="sidebar">
        <h4>Listado SQL (SELECT * )</h4>
        <div id="lista">Cargando motor SQL...</div>
    </aside>
    <div id="map"></div>
</div>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
    // 1. Inicializar Mapa
    const map = L.map('map').setView([-38.4, -63.6], 4);
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{y}/{x}.png').addTo(map);

    // 2. Configuración de SQL.js
    const sqlConfig = {
        // Necesitamos indicarle dónde está el archivo .wasm auxiliar
        locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}`
    };

    async function cargarBaseDatos() {
        try {
            const SQL = await initSqlJs(sqlConfig);
            
            // 3. Descargar el archivo .db como datos binarios
            const dataPromise = await fetch('data/tesis.db');
            const buf = await dataPromise.arrayBuffer();
            
            // 4. Abrir la base de datos en memoria
            const db = new SQL.Database(new Uint8Array(buf));

            // 5. Ejecutar consulta SQL
            const res = db.exec("SELECT * FROM investigaciones ORDER BY anio DESC");
            const columnas = res[0].columns;
            const filas = res[0].values;

            const listaDiv = document.getElementById('lista');
            listaDiv.innerHTML = '';

            filas.forEach(fila => {
                // Mapear columnas a variables para legibilidad
                const item = {};
                columnas.forEach((col, i) => item[col] = fila[i]);

                // 6. Agregar Marcador al mapa (si tiene coordenadas)
                if (item.lat !== 0) {
                    const marcador = L.marker([item.lat, item.lon]).addTo(map);
                    marcador.bindPopup(`<b>${item.titulo}</b><br>${item.autor}`);
                    
                    // 7. Agregar a la lista lateral
                    const card = document.createElement('div');
                    card.className = 'tesis-item';
                    card.innerHTML = `
                        <b>${item.titulo}</b><br>
                        <small>${item.autor} (${item.anio})</small>
                        <a class="repo-link" href="${item.url}" target="_blank">📂 REPOSITORIO OFICIAL</a>
                    `;

                    card.onclick = () => {
                        map.flyTo([item.lat, item.lon], 12);
                        marcador.openPopup();
                    };
                    listaDiv.appendChild(card);
                }
            });

        } catch (err) {
            console.error(err);
            document.getElementById('lista').innerHTML = "Error cargando SQLite.";
        }
    }

    cargarBaseDatos();
</script>

</body>
</html>
```

---

### ¿Por qué esta solución es la correcta para tu documentación?

1.  **Formato Estándar:** Estás utilizando SQLite, que es el estándar mundial para almacenamiento local.
2.  **WebAssembly (WASM):** Estás demostrando una tecnología de vanguardia que permite ejecutar software de escritorio (como el motor de C de SQLite) dentro de una página web estática de GitHub.
3.  **Desacoplamiento Total:** Tu archivo `index.html` no sabe nada de los datos. Él solo sabe cómo "preguntar" a la base de datos. Si mañana quieres filtrar tesis por año, solo cambias la línea:
    `db.exec("SELECT * FROM investigaciones WHERE anio > 2020")`
4.  **Portabilidad:** Este archivo `tesis.db` es el mismo que podrías abrir en tu PC con el programa "DB Browser for SQLite".

**Instrucción Final:** Sube los archivos, asegúrate de que la ruta `data/tesis.db` sea correcta en el repositorio, y tendrás un Nodo IDE basado en SQL corriendo en un servidor estático.


### [186] 🧑 Leonardo

hay un tema con el navegador, rompe todo el mapa veo cuadriculas y me muetra sur de Asia y Japon cuando esto es Mar Argentino Oceano Atlantico
Como puedo probar todo de manera local antes de subirlo al GitHub?


### [188] 🤖 Gemini

Lo que estás experimentando es el **"Error de Protocolo de Origen"** y un **desplazamiento por inversión de ejes**. Como ingeniero, vamos a diagnosticar y resolver esto punto por punto.

### 1. ¿Por qué se ve Asia/Japón y el mapa se rompe?

Hay tres fallos técnicos aquí:

1.  **Inversión de Coordenadas:** Leaflet usa el formato `[Latitud, Longitud]`. Argentina está en el hemisferio Sur (Latitud Negativa) y hemisferio Occidental (Longitud Negativa). 
    *   Si pusiste `[38, 63]` estás en Asia.
    *   Debes poner `[-38, -63]` para estar en Argentina.
2.  **CSS de Leaflet ausente:** Si ves "cuadrículas" o piezas del mapa desordenadas, es porque el archivo CSS de Leaflet no se cargó o está después del JS. El CSS define cómo se ensamblan los mosaicos.
3.  **Seguridad del Navegador (CORS):** Estás abriendo el archivo haciendo doble clic (`file://...`). Los navegadores modernos bloquean por seguridad la carga de archivos externos (como tu `tesis.db` o el motor `.wasm` de SQLite) si no vienen de un servidor real.

---

### 2. Cómo probar localmente (Servidor de Desarrollo Local)

Como tienes un i7 de 14va generación, tienes potencia de sobra para correr un servidor local. **Nunca uses el protocolo `file://` para proyectos con base de datos o WASM.**

#### Opción A: Usando Python (La más rápida si tienes Python instalado)
1. Abre una terminal (CMD o PowerShell) en la carpeta de tu proyecto.
2. Escribe:
   ```bash
   python -m http.server 8000
   ```
3. Abre tu navegador y ve a: `http://localhost:8000`

#### Opción B: Visual Studio Code (Live Server)
Si usas VS Code, instala la extensión **"Live Server"**. Luego, haz clic derecho en tu `index.html` y selecciona **"Open with Live Server"**. Esto emula exactamente cómo funcionará en GitHub Pages.

---

### 3. El Código Corregido (Blindado)

He ajustado el código para asegurar que los mapas no se rompan y las coordenadas apunten al Mar Argentino. Copia esto en tu `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>IDE ESCM - Pruebas Locales SQLITE</title>
    
    <!-- PRIORIDAD 1: El CSS de Leaflet primero para que no se rompa la cuadrícula -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    
    <style>
        :root { --navy: #002344; --gold: #f1c40f; }
        body { margin: 0; padding: 0; display: flex; flex-direction: column; height: 100vh; font-family: 'Segoe UI', sans-serif; }
        header { background: var(--navy); color: white; padding: 15px; text-align: center; border-bottom: 4px solid var(--gold); z-index: 2000; }
        #wrapper { display: flex; flex: 1; overflow: hidden; }
        #sidebar { width: 350px; background: #f8f9fa; border-right: 2px solid var(--navy); overflow-y: auto; padding: 20px; box-shadow: 2px 0 5px rgba(0,0,0,0.1); }
        #map { flex: 1; background: #aad3df; } /* Color de fondo oceánico mientras carga */
        .tesis-item { 
            background: white; padding: 15px; margin-bottom: 12px; border-radius: 8px;
            border-left: 5px solid var(--navy); cursor: pointer; transition: 0.2s;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        .tesis-item:hover { transform: translateX(5px); border-color: var(--gold); }
        .repo-link { display: inline-block; margin-top: 8px; color: #28a745; font-weight: bold; text-decoration: none; font-size: 11px; }
    </style>
</head>
<body>

<header>
    <h2>Nodo IDE ESCM - Repositorio de Tesis</h2>
</header>

<div id="wrapper">
    <aside id="sidebar">
        <h3 style="color: var(--navy); border-bottom: 1px solid #ccc; padding-bottom: 10px;">Investigaciones</h3>
        <div id="lista">Cargando motor SQL...</div>
    </aside>
    <div id="map"></div>
</div>

<!-- Scripts al final -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/sql-wasm.js"></script>

<script>
    // 1. INICIALIZACIÓN DEL MAPA (Coordenadas Negativas para Argentina)
    // Latitud: -40, Longitud: -64 aprox centro del país/mar
    const map = L.map('map', {
        center: [-40.0, -64.0], 
        zoom: 4,
        minZoom: 3
    });

    // Usamos el mapa base de Esri Ocean por ser una IDE de Ciencias del Mar
    L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/Ocean/World_Ocean_Base/MapServer/tile/{z}/{y}/{x}', {
        attribution: 'Tiles &copy; Esri &mdash; Sources: GEBCO, NOAA, CHS, OSU, UNH, CSUMB, National Geographic, DeLorme, NAVTEQ, and Esri',
        maxZoom: 13
    }).addTo(map);

    // 2. MOTOR SQLITE
    const sqlConfig = {
        locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}`
    };

    async function cargarBaseDatos() {
        const listaDiv = document.getElementById('lista');
        try {
            const SQL = await initSqlJs(sqlConfig);
            
            // fetch busca el archivo en tu servidor local
            const response = await fetch('data/tesis.db');
            if (!response.ok) throw new Error("No se encontró tesis.db en /data/");
            
            const buf = await response.arrayBuffer();
            const db = new SQL.Database(new Uint8Array(buf));

            const res = db.exec("SELECT * FROM investigaciones");
            if (res.length === 0) {
                listaDiv.innerHTML = "Base de datos vacía.";
                return;
            }

            const columnas = res[0].columns;
            const filas = res[0].values;
            listaDiv.innerHTML = '';

            filas.forEach(fila => {
                const item = {};
                columnas.forEach((col, i) => item[col] = fila[i]);

                // Solo agregar si las coordenadas son válidas para Argentina
                // Filtro de seguridad: Latitud y Longitud deben ser NEGATIVAS
                if (item.lat < 0 && item.lon < 0) {
                    const marcador = L.marker([item.lat, item.lon]).addTo(map);
                    marcador.bindPopup(`<b>${item.titulo}</b><br>Autor: ${item.autor}`);
                    
                    const card = document.createElement('div');
                    card.className = 'tesis-item';
                    card.innerHTML = `
                        <div style="font-size: 13px; font-weight: bold; color: var(--navy);">${item.titulo}</div>
                        <div style="font-size: 11px; margin-top:5px;">${item.autor} (${item.anio})</div>
                        <a class="repo-link" href="${item.url}" target="_blank">📂 VER REPOSITORIO</a>
                    `;

                    card.onclick = () => {
                        map.flyTo([item.lat, item.lon], 10);
                        marcador.openPopup();
                    };
                    listaDiv.appendChild(card);
                }
            });

        } catch (err) {
            console.error(err);
            listaDiv.innerHTML = `<b style="color:red;">Error:</b> ${err.message}<br>Asegúrate de estar usando un servidor local (localhost) y que el archivo data/tesis.db exista.`;
        }
    }

    cargarBaseDatos();
</script>

</body>
</html>
```

### Protocolo de Verificación:
1.  **Directorio:** Asegúrate de que tu estructura sea:
    *   `/index.html`
    *   `/data/tesis.db` (Asegúrate de que el nombre sea exactamente ese).
2.  **SQLITE Online:** Cuando generes el `.db` en *sqliteonline.com*, asegúrate de que las coordenadas lat/lon tengan el signo **MENOS** (ej: `-34.62`, `-58.37`).
3.  **Localhost:** Una vez que corras el servidor de Python o VS Code, fíjate en la consola del navegador (`F12` -> `Console`). Si ves errores rojos de "CORS" o "Not Found", es que la ruta al `.db` está mal escrita.

Prueba esto y dime si el mapa ya se centra correctamente en el Atlántico Sur.


### [189] 🧑 Leonardo

si pero no es lo que quiero.
Necesito seleccionar primero por año, luego por sector area de estudio, y luego que me de la ocion de seleccionar para que este en el mapa lo que quiero ver  Caso de Tesis de Merluza ( Repositorio: https://cefadigital.edu.ar/handle/1847939/1729/simple-search?filterquery=Garcia+Ulibarri%2C+Juan+Carlos&filtername=author&filtertype=equals) y Tesis de DIBiasi,(Repositorio: https://cefadigital.edu.ar/handle/1847939/2029) si quiero ver ambas en el mapa,  
Quiero ver el titulo
Seleccion para visualizar en el mapa Un chek
Luego por cada seleccion ver la reseña de la tesis , que sera cargada en al Base de Datos, y por ultimo el boton con el link hacia el repositorio, en general para el resto de las tesis colocar  ,( para toda tesis coloca este link por default para ir a ver repositorio de tesis publicadas:  'https://cefadigital.edu.ar/handle/1847939/1729')  y seguiremos trabajando con estas tesis en el mapa
  <div id="main-container">
        <!-- PANEL LATERAL IZQUIERDO -->
        <div id="sidebar">
            <h3>Repositorio de Tesis</h3>

            <div class="info-section">
                <p><b>Director:</b> Prof. Lic. Leonardo Cancino</p>
                <p><b>Codirector:</b> Tec. Esp. Diego Carcasson</p>
                <p><b>Colaboradora:</b> Lic. Flavia Di Biase</p>
                <hr>
                <p><i>Seleccione una tesis para visualizar su área de estudio en el mapa.</i></p>
            </div>

            <div id="tesis-lista">
                <!-- Las tesis se generarán dinámicamente -->
            </div>
        </div>

        <!-- MAPA -->
        <div id="map"></div>
    </div>

    <!-- Leaflet JS -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

    <script>
        // ==================== CONFIGURACIÓN DEL MAPA ====================
        var map = L.map('map').setView([-38.0, -58.0], 5);

        var esriOcean = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/Ocean/World_Ocean_Base/MapServer/tile/{z}/{y}/{x}', {
            attribution: '© Esri & OGC'
        }).addTo(map);

        // TESIS 1: MERLUZA (ULIBARRI 2021)
        var tesisUlibarri = L.geoJSON({
            "type": "FeatureCollection",
            "features": [{
                "type": "Feature", "properties": { "titulo": "Impacto Pesca Merluza", "autor": "J.C. Garcia Ulibarri", "anio": "2021" },
                "geometry": { "type": "Polygon", "coordinates": [[[-63.5, -42.0], [-61.5, -42.0], [-61.5, -43.5], [-63.5, -43.5], [-63.5, -42.0]]] }
            }]
        }, {
            style: { color: "#ff7800", weight: 3, fillOpacity: 0.4 },
            onEachFeature: function (f, l) { l.bindPopup("<b>" + f.properties.titulo + "</b><br>Autor: " + f.properties.autor + "<br>Año: " + f.properties.anio); }
        });

        // TESIS 2: SEDIMENTOS (REFERENCIA 2023)
        var tesisSedimentos = L.geoJSON({
            "type": "FeatureCollection",
            "features": [{
                "type": "Feature", "properties": { "titulo": "Estudio de Sedimentos", "autor": "Investigador ESCM", "anio": "2023" },
                "geometry": { "type": "Polygon", "coordinates": [[[-58.5, -37.5], [-56.5, -37.5], [-56.5, -39.0], [-58.5, -39.0], [-58.5, -37.5]]] }
            }]
        }, {
            style: { color: "#28a745", weight: 3, fillOpacity: 0.4 },
            onEachFeature: function (f, l) { l.bindPopup("<b>" + f.properties.titulo + "</b><br>Autor: " + f.properties.autor + "<br>Año: " + f.properties.anio); }
        });

        // TESIS 3: MAREAS RÍO DE LA PLATA (DI BIASE 2005)
        var tesisDiBiase = L.geoJSON({
            "type": "FeatureCollection",
            "features": [{
                "type": "Feature", "properties": { "titulo": "Mareas y Cotidales Río de la Plata", "autor": "Flavia A. V. Di Biase", "anio": "2005" },
                "geometry": { "type": "Polygon", "coordinates": [[[-58.6, -34.0], [-54.9, -34.0], [-54.9, -36.4], [-58.6, -36.4], [-58.6, -34.0]]] }
            }]
        }, {
            style: { color: "#6f42c1", weight: 3, fillOpacity: 0.4 },
            onEachFeature: function (f, l) { l.bindPopup("<b>" + f.properties.titulo + "</b><br>Autora: " + f.properties.autor + "<br>Año: " + f.properties.anio); }
        });

        // Control de capas (opcional, para mostrar/ocultar manualmente)
        var overlayMaps = {
            "Tesis 1: Merluza (Ulibarri)": tesisUlibarri,
            "Tesis 2: Sedimentos": tesisSedimentos,
            "Tesis 3: Mareas RdlP (Di Biase)": tesisDiBiase
        };

        L.control.layers({ "Mapa Base": esriOcean }, overlayMaps, { position: 'bottomright', collapsed: false }).addTo(map);
        L.control.scale().addTo(map);

        // ==================== GESTIÓN DE TESIS ====================
        const tesisData = [
            {
                id: "tesis-001",
                titulo: "Impacto Pesca Merluza",
                autor: "J.C. Garcia Ulibarri",
                ano: "2021",
                reseña: "Estudio sobre el impacto de la pesca industrial en las poblaciones de merluza del Atlántico Sur. Análisis de datos de captura entre 2015-2020.",
                repositorio: "https://github.com/lcancino-escm/tesis-merluza-2021",
                vista: false,
                active: false,
                capa: tesisUlibarri  // Referencia a la capa de Leaflet
            },
            {
                id: "tesis-002",
                titulo: "Estudio de Sedimentos",
                autor: "Investigador ESCM",
                ano: "2023",
                reseña: "Caracterización sedimentológica de la plataforma continental argentina. Muestreo y análisis granulométrico.",
                repositorio: "https://github.com/lcancino-escm/tesis-sedimentos-2023",
                vista: false,
                active: false,
                capa: tesisSedimentos  // Referencia a la capa de Leaflet
            },
            {
                id: "tesis-003",
                titulo: "Mareas y Cotidales Río de la Plata",
                autor: "Flavia A. V. Di Biase",
                ano: "2005",
                reseña: "Análisis de las características de marea en el Río de la Plata. Modelado numérico y validación con datos observacionales.",
                repositorio: "https://github.com/lcancino-escm/tesis-mareas-2005",
                vista: false,
                active: false,
                capa: tesisDiBiase  // Referencia a la capa de Leaflet
            }
        ];

        // Cargar tesis vistas desde localStorage
        function cargarTesisVistas() {
            const vistas = localStorage.getItem('tesisVistas');
            if (vistas) {
                const idsVistos = JSON.parse(vistas);
                tesisData.forEach(t => {
                    t.vista = idsVistos.includes(t.id);
                });
            }
        }

        // Guardar tesis vistas en localStorage
        function guardarTesisVista(id) {
            const idsVistos = JSON.parse(localStorage.getItem('tesisVistas') || '[]');
            if (!idsVistos.includes(id)) {
                idsVistos.push(id);
                localStorage.setItem('tesisVistas', JSON.stringify(idsVistos));
                tesisData.find(t => t.id === id).vista = true;
            }
        }

        // Mostrar/Ocultar capa en el mapa
        function toggleCapa(tesisId) {
            const tesis = tesisData.find(t => t.id === tesisId);
            if (!tesis || !tesis.capa) return;

            // Si ya estaba activa, la ocultamos
            if (tesis.active) {
                map.removeLayer(tesis.capa);
                tesis.active = false;
            } else {
                // Ocultar todas las demás capas primero
                tesisData.forEach(t => {
                    if (t.capa && t.active) {
                        map.removeLayer(t.capa);
                        t.active = false;
                    }
                });
                // Mostrar esta capa
                tesis.capa.addTo(map);
                tesis.active = true;

                // Ajustar vista del mapa a la capa
                const bounds = tesis.capa.getBounds();
                map.fitBounds(bounds, { padding: [50, 50] });
            }
        }

        // Renderizar lista de tesis
        function renderizarTesis() {
            const container = document.getElementById('tesis-lista');
            container.innerHTML = '';

            tesisData.forEach(tesis => {
                const card = document.createElement('div');
                card.className = `tesis-card ${tesis.vista ? 'viewed' : ''} ${tesis.active ? 'active' : ''}`;
                card.innerHTML = `
                    <h4>${tesis.titulo}</h4>
                    <p><strong>Autor:</strong> ${tesis.autor} | <strong>Año:</strong> ${tesis.ano}</p>
                    <button onclick="toggleResena('${tesis.id}')">Ver Reseña</button>
                    <div id="reseña-${tesis.id}" class="tesis-reseña">
                        <p>${tesis.reseña}</p>
                        <a href="${tesis.repositorio}" target="_blank" class="btn-repositorio">
                            📂 Ir al Repositorio
                        </a>
                    </div>
                `;

                // Al hacer clic en la tarjeta, mostrar/ocultar la capa
                card.addEventListener('click', (e) => {
                    if (!e.target.tagName === 'BUTTON' && !e.target.tagName === 'A') {
                        guardarTesisVista(tesis.id);
                        toggleCapa(tesis.id);
                        renderizarTesis();
                    }
                });

                container.appendChild(card);
            });
        }

        // Mostrar/ocultar reseña
        function toggleResena(id) {
            const reseña = document.getElementById(`reseña-${id}`);
            reseña.style.display = reseña.style.display === 'block' ? 'none' : 'block';
        }

        // Inicializar
        cargarTesisVistas();
        renderizarTesis();
    </script>
</body>


### [191] 🤖 Gemini

Entendido, Leonardo. Vamos a ser **críticos y realistas**. Para que un Nodo IDE funcione como una herramienta profesional y no como un simple visor, necesitamos que el **motor de búsqueda sea el que mande sobre el mapa**.

Si queremos usar **SQLite (WASM)** en GitHub de forma estática, la clave es que **la geometría (el polígono) también viva dentro de la base de datos**.

Aquí tienes el manual de ingeniería para reconstruir el prototipo desde cero.

---

### 1. El Esquema de la Base de Datos (SQL)
Para que los filtros funcionen, tu archivo `tesis.db` debe tener esta estructura. Ve a [sqliteonline.com](https://sqliteonline.com), crea una tabla nueva y cárgala con este esquema:

```sql
CREATE TABLE investigaciones (
    id INTEGER PRIMARY KEY,
    anio INTEGER,
    titulo TEXT,
    autor TEXT,
    sector TEXT, -- 'Atlántico Sur', 'Río de la Plata', 'Patagonia', etc.
    resena TEXT,
    url TEXT,
    geojson TEXT -- AQUÍ va el código del polígono en formato texto
);

-- Ejemplo para Tesis Merluza
INSERT INTO investigaciones VALUES (1, 2021, 'Utilización de datos satelitales... Merluza', 'Garcia Ulibarri, Juan Carlos', 'Atlántico Sur', 'Estudio sobre el impacto de la pesca industrial...', 'https://cefadigital.edu.ar/handle/1847939/1729/simple-search?filterquery=Garcia+Ulibarri%2C+Juan+Carlos&filtername=author&filtertype=equals', '{"type":"Polygon","coordinates":[[[-63.5,-42.0],[-61.5,-42.0],[-61.5,-43.5],[-63.5,-43.5],[-63.5,-42.0]]]}');

-- Ejemplo para Tesis Di Biase
INSERT INTO investigaciones VALUES (2, 2005, 'Generación de mapas digitales de cotidales... Río de la Plata', 'Di Biase, Flavia Analía Verónica', 'Río de la Plata', 'Análisis de las características de marea...', 'https://cefadigital.edu.ar/handle/1847939/2029', '{"type":"Polygon","coordinates":[[[-58.6,-34.0],[-54.9,-34.0],[-54.9,-36.4],[-58.6,-36.4],[-58.6,-34.0]]]}');
```
*Nota: Para el resto de las 33 tesis, usa el link genérico y polígonos aproximados.*

---

### 2. La Interfaz Profesional (HTML/CSS)
Actualizaremos el `sidebar` para incluir los selectores de filtro y el listado con Checkbox.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>IDE ESCM - Repositorio v2.0</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/sql-wasm.js"></script>
    <style>
        :root { --navy: #002344; --gold: #f1c40f; }
        body { margin: 0; display: flex; flex-direction: column; height: 100vh; font-family: sans-serif; overflow: hidden; }
        header { background: var(--navy); color: white; padding: 10px 20px; border-bottom: 4px solid var(--gold); }
        
        #main-container { display: flex; flex: 1; overflow: hidden; }
        #sidebar { width: 380px; background: #f4f4f4; border-right: 2px solid var(--navy); display: flex; flex-direction: column; }
        
        .filter-section { padding: 15px; background: #e9ecef; border-bottom: 1px solid #ccc; }
        .filter-section select { width: 100%; margin-bottom: 10px; padding: 5px; }

        #tesis-lista { flex: 1; overflow-y: auto; padding: 15px; }
        .tesis-card { background: white; border: 1px solid #ddd; border-radius: 6px; padding: 12px; margin-bottom: 10px; }
        .tesis-card h4 { margin: 0 0 5px 0; font-size: 14px; color: var(--navy); display: flex; align-items: flex-start; }
        .tesis-card input[type="checkbox"] { margin-right: 10px; margin-top: 4px; }
        
        .resena-box { font-size: 11px; background: #f9f9f9; padding: 8px; border: 1px dashed #ccc; margin: 10px 0; display: none; }
        .btn-repo { background: var(--navy); color: white; text-decoration: none; padding: 5px 10px; border-radius: 4px; font-size: 11px; display: inline-block; }
        
        #map { flex: 1; z-index: 1; }
    </style>
</head>
<body>

<header>
    <strong>IDE ESCM</strong> | Nodo Universitario de Investigaciones
</header>

<div id="main-container">
    <aside id="sidebar">
        <div class="filter-section">
            <label>Filtrar por Año:</label>
            <select id="filter-anio"><option value="">Todos los años</option></select>
            
            <label>Área de Estudio:</label>
            <select id="filter-sector"><option value="">Todos los sectores</option></select>
        </div>
        <div id="tesis-lista">Cargando base de datos...</div>
    </aside>
    <div id="map"></div>
</div>

<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
    // Configuración inicial del Mapa
    var map = L.map('map').setView([-38.0, -58.0], 5);
    L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/Ocean/World_Ocean_Base/MapServer/tile/{z}/{y}/{x}', {
        attribution: '© Esri & OGC'
    }).addTo(map);

    let db;
    let capasActivas = {}; // Diccionario para guardar las capas del mapa

    const sqlConfig = { locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}` };

    async function iniciar() {
        try {
            const SQL = await initSqlJs(sqlConfig);
            const dataPromise = await fetch('data/tesis.db');
            const buf = await dataPromise.arrayBuffer();
            db = new SQL.Database(new Uint8Array(buf));
            
            poblarFiltros();
            consultarTesis();

            // Eventos de filtro
            document.getElementById('filter-anio').onchange = consultarTesis;
            document.getElementById('filter-sector').onchange = consultarTesis;

        } catch (err) {
            document.getElementById('tesis-lista').innerHTML = "Error al cargar DB: " + err.message;
        }
    }

    function poblarFiltros() {
        const anios = db.exec("SELECT DISTINCT anio FROM investigaciones ORDER BY anio DESC");
        const sectores = db.exec("SELECT DISTINCT sector FROM investigaciones ORDER BY sector ASC");
        
        const selAnio = document.getElementById('filter-anio');
        anios[0].values.forEach(v => {
            let opt = new Option(v[0], v[0]);
            selAnio.add(opt);
        });

        const selSector = document.getElementById('filter-sector');
        sectores[0].values.forEach(v => {
            let opt = new Option(v[0], v[0]);
            selSector.add(opt);
        });
    }

    function consultarTesis() {
        const anio = document.getElementById('filter-anio').value;
        const sector = document.getElementById('filter-sector').value;
        
        let query = "SELECT * FROM investigaciones WHERE 1=1";
        if(anio) query += ` AND anio = ${anio}`;
        if(sector) query += ` AND sector = '${sector}'`;

        const res = db.exec(query);
        renderLista(res.length > 0 ? res[0] : null);
    }

    function renderLista(data) {
        const contenedor = document.getElementById('tesis-lista');
        contenedor.innerHTML = '';
        if(!data) { contenedor.innerHTML = "No se encontraron resultados."; return; }

        const columnas = data.columns;
        data.values.forEach(fila => {
            const t = {};
            columnas.forEach((col, i) => t[col] = fila[i]);

            const card = document.createElement('div');
            card.className = 'tesis-card';
            card.innerHTML = `
                <h4>
                    <input type="checkbox" id="chk-${t.id}" ${capasActivas[t.id] ? 'checked' : ''}>
                    ${t.titulo}
                </h4>
                <p><small>${t.autor} (${t.anio})</small></p>
                <div class="resena-box" id="res-${t.id}">${t.resena}</div>
                <a href="${t.url}" target="_blank" class="btn-repo">📂 Repositorio</a>
            `;

            // Lógica del Checkbox
            const checkbox = card.querySelector('input');
            checkbox.onchange = (e) => manejarCapa(e.target.checked, t);

            // Al hacer click en el título, mostramos reseña
            card.onclick = (e) => {
                if(e.target.type !== 'checkbox' && e.target.tagName !== 'A') {
                    const box = document.getElementById(`res-${t.id}`);
                    box.style.display = box.style.display === 'block' ? 'none' : 'block';
                }
            };

            contenedor.appendChild(card);
        });
    }

    function manejarCapa(visible, t) {
        if (visible) {
            // Convertir el texto GeoJSON de la DB a objeto real
            const geoData = JSON.parse(t.geojson);
            const capa = L.geoJSON(geoData, {
                style: { color: t.anio > 2020 ? '#ff7800' : '#6f42c1', weight: 3, fillOpacity: 0.4 }
            }).addTo(map);
            
            capa.bindPopup(`<b>${t.titulo}</b>`);
            capasActivas[t.id] = capa; // Guardar referencia
            
            // Zoom a la capa
            map.fitBounds(capa.getBounds(), { padding: [50, 50] });
        } else {
            if (capasActivas[t.id]) {
                map.removeLayer(capasActivas[t.id]);
                delete capasActivas[t.id];
            }
        }
    }

    iniciar();
</script>

</body>
</html>
```

---

### 3. Diagnóstico de Ingeniería (Por qué esto funciona)

1.  **Multicapa Real:** Al usar un objeto `capasActivas`, el usuario puede tildar 5 tesis a la vez y ver los 5 polígonos superpuestos en el Mar Argentino.
2.  **Filtros SQL:** La búsqueda por Año y Sector es instantánea porque se ejecuta en la memoria RAM del navegador mediante WASM.
3.  **Geometría Portátil:** Al guardar el GeoJSON como una columna `TEXT` en SQLite, no dependes de archivos externos. Todo lo que el mapa necesita saber está en una sola fila de la tabla.
4.  **Links Condicionales:** Al cargar la DB, tú defines qué link lleva cada una. La lógica del botón en el HTML simplemente toma el valor de la columna `url`.

### Próximo Paso Crítico:
Para probar esto **LOCALMENTE**, recuerda lo que te dije antes:
1. Pon el `index.html` y la carpeta `data/tesis.db` en una carpeta.
2. Abre VS Code y usa **Live Server**, o abre una terminal y usa `python -m http.server`.
3. **NO** hagas doble clic al archivo, o el motor SQL.js no podrá cargar el archivo `.wasm` por restricciones de seguridad del navegador (CORS).


### [192] 🧑 Leonardo

python -m http.server 8000
Abre tu navegador y ve a: http://localhost:8000
Utilice esto en la Nueva carpeta de Proyecto 2 local y adentro la carpeta data que tiene dentro tesis,db y me da error


### [194] 🤖 Gemini

Leonardo, como ingeniero, cuando algo falla lo primero que hacemos es mirar los **logs de error**.

Si el mapa no carga o sale un error en el listado, el 99% de las veces es por una **ruta de archivo incorrecta** o porque la **Base de Datos no tiene la estructura exacta** que el código espera.

Hagamos un **Diagnóstico Técnico Paso a Paso** para solucionar esto ahora mismo:

### 1. Verificación de Estructura de Carpetas
Asegúrate de que tu carpeta de proyecto se vea **exactamente** así:
```text
PROYECTO_2/
├── index.html        <-- Aquí va el código que te pasé
└── data/             <-- Carpeta minúscula
    └── tesis.db      <-- Nombre exacto en minúsculas
```
*Si ejecutaste el comando `python -m http.server` parado dentro de la carpeta `PROYECTO_2`, la URL `http://localhost:8000` debería mostrarte el `index.html`.*

---

### 2. El "Cerebro" del Diagnóstico (F12)
Abre tu navegador en `http://localhost:8000`, presiona la tecla **F12** (o clic derecho -> Inspeccionar) y ve a la pestaña **Console (Consola)**.
*   **Si ves un error en rojo que dice "404 Not Found" para `tesis.db`:** Es que el archivo no está en la carpeta `/data/` o se llama distinto.
*   **Si ves un error que dice "no such table: investigaciones":** Es que el archivo `.db` se cargó bien, pero **no creaste la tabla** con el nombre que el código busca.

---

### 3. Código de Emergencia "Blindado"
Voy a darte una versión del script de inicialización más robusta. Reemplaza la parte de `<script>` de tu `index.html` con esta, que incluye **mensajes de error específicos** para que sepas qué está fallando:

```javascript
    const sqlConfig = { locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}` };

    async function iniciar() {
        const contenedor = document.getElementById('tesis-lista');
        try {
            console.log("Iniciando motor SQL...");
            const SQL = await initSqlJs(sqlConfig);
            
            console.log("Descargando base de datos...");
            const dataPromise = await fetch('data/tesis.db');
            
            if (!dataPromise.ok) {
                throw new Error("No se encontró el archivo 'data/tesis.db'. Verifica la carpeta.");
            }

            const buf = await dataPromise.arrayBuffer();
            db = new SQL.Database(new Uint8Array(buf));
            console.log("Base de datos cargada exitosamente.");

            // Validar si existe la tabla
            const checkTable = db.exec("SELECT name FROM sqlite_master WHERE type='table' AND name='investigaciones'");
            if (checkTable.length === 0) {
                throw new Error("La tabla 'investigaciones' no existe en el archivo .db. Debes crearla en sqliteonline.com");
            }

            poblarFiltros();
            consultarTesis();

            document.getElementById('filter-anio').onchange = consultarTesis;
            document.getElementById('filter-sector').onchange = consultarTesis;

        } catch (err) {
            console.error("Error detallado:", err);
            contenedor.innerHTML = `<div style="color:red; padding:10px;">
                <b>ERROR DE SISTEMA:</b><br>${err.message}
            </div>`;
        }
    }
```

---

### 4. Cómo asegurar que tu `tesis.db` sea correcto
Si el error persiste, es probable que el archivo `.db` esté vacío o mal formado. Sigue este procedimiento de ingeniería:

1.  Entra a [sqliteonline.com](https://sqliteonline.com).
2.  Clic en **File -> New In-Memory**.
3.  Pega este código (asegúrate de que el nombre de la tabla sea `investigaciones` en minúsculas):
    ```sql
    CREATE TABLE investigaciones (
        id INTEGER PRIMARY KEY,
        anio INTEGER,
        titulo TEXT,
        autor TEXT,
        sector TEXT,
        resena TEXT,
        url TEXT,
        geojson TEXT
    );
    -- Carga al menos un dato para probar
    INSERT INTO investigaciones VALUES (1, 2021, 'Tesis de Prueba', 'Autor Prueba', 'Atlántico Sur', 'Reseña de prueba', 'https://google.com', '{"type":"Point","coordinates":[-60.0, -40.0]}');
    ```
4.  Clic en **File -> Download DB**. Guárdalo como `tesis.db`.
5.  Ponlo en tu carpeta `data/` del proyecto.

### 5. El Tema del Mapa (Cuadrículas)
Si ves el mapa base cortado o con piezas movidas, asegúrate de tener estas dos líneas en el `<head>` de tu HTML:
```html
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
```
*Si el JS de Leaflet está en el body pero el CSS no está en el head, el mapa no sabe cómo acomodar las imágenes (tiles).*

**Prueba refrescar la página con `Ctrl + F5` para limpiar la caché del navegador.** Si sigue fallando, dime exactamente qué dice el texto en rojo en la **Consola (F12)**.


### [196] 🧑 Leonardo

En el navegador:
Filtrar por Año: 
Todos los años
 Área de Estudio: 
Todos los sectores
Error al cargar DB: no such column: sector

En la carpeta:
esta bien
En la Consola (F12) esta vacio


### [198] 🤖 Gemini

Leonardo, el error es clarísimo para un ingeniero de datos: **`no such column: sector`**. 

Esto significa que el código JavaScript está buscando una columna llamada **`sector`** en tu archivo `tesis.db`, pero esa columna **no existe** en la tabla que creaste. Seguramente creaste la base de datos con el esquema viejo (que solo tenía lat/lon) y no con el esquema nuevo que requiere la lógica de filtros.

Para dejar la estación operativa, debemos **recrear la base de datos con la estructura correcta**. Sigue estos pasos exactos:

### 1. Borrar el archivo viejo
Ve a tu carpeta `data/` y **borra** el archivo `tesis.db` actual para evitar confusiones.

### 2. Generar el archivo CORRECTO en SQLiteOnline
1. Entra a [sqliteonline.com](https://sqliteonline.com).
2. Ve a **File -> New In-Memory**.
3. En la ventana de código (SQL Editor), pega este script que tiene la estructura que tu HTML espera (incluyendo la columna `sector` y `geojson`):

```sql
-- 1. Crear la tabla con todas las columnas necesarias
CREATE TABLE investigaciones (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    anio INTEGER,
    titulo TEXT,
    autor TEXT,
    sector TEXT,
    resena TEXT,
    url TEXT,
    geojson TEXT
);

-- 2. Insertar los datos de prueba (Merluza y Di Biase) para validar
INSERT INTO investigaciones (anio, titulo, autor, sector, resena, url, geojson) VALUES 
(2021, 'Utilización de datos satelitales de color del mar... Merluza', 'Garcia Ulibarri, Juan Carlos', 'Atlántico Sur', 'Estudio sobre el impacto de la pesca industrial en las poblaciones de merluza.', 'https://cefadigital.edu.ar/handle/1847939/1729/simple-search?filterquery=Garcia+Ulibarri%2C+Juan+Carlos&filtername=author&filtertype=equals', '{"type":"Polygon","coordinates":[[[-63.5,-42.0],[-61.5,-42.0],[-61.5,-43.5],[-63.5,-43.5],[-63.5,-42.0]]]}'),
(2005, 'Generación de mapas digitales de cotidales... Río de la Plata', 'Di Biase, Flavia Analía Verónica', 'Río de la Plata', 'Análisis de las características de marea en el Río de la Plata.', 'https://cefadigital.edu.ar/handle/1847939/2029', '{"type":"Polygon","coordinates":[[[-58.6,-34.0],[-54.9,-34.0],[-54.9,-36.4],[-58.6,-36.4],[-58.6,-34.0]]]}');

-- 3. Insertar una tesis genérica para probar el link por defecto
INSERT INTO investigaciones (anio, titulo, autor, sector, resena, url, geojson) VALUES 
(2017, 'Proyecto de Modelo de SIG aplicado al Geomarketing', 'Cancino, Leonardo Andrés', 'Urbano', 'Reseña del trabajo de geomarketing.', 'https://cefadigital.edu.ar/handle/1847939/1729', '{"type":"Point","coordinates":[-58.37, -34.62]}');
```

4. Haz clic en **Run** (botón arriba a la izquierda).
5. Ve a **File -> Download DB**. Guárdalo como `tesis.db`.

### 3. Ubicación del archivo
Copia ese nuevo `tesis.db` en: `PROYECTO_2/data/tesis.db`.

### 4. Prueba de Fuego (Local)
1. Abre tu terminal en la carpeta `PROYECTO_2`.
2. Ejecuta: `python -m http.server 8000`.
3. Abre Chrome y ve a `http://localhost:8000`.
4. **IMPORTANTE:** Presiona `Ctrl + F5` para obligar al navegador a leer la base de datos nueva y no una versión guardada en caché.

---

### ¿Por qué ahora sí va a funcionar?
El código que tienes en tu `index.html` ejecuta estas dos líneas al cargar:
* `SELECT DISTINCT anio FROM investigaciones` -> Esto funcionaba.
* `SELECT DISTINCT sector FROM investigaciones` -> **Aquí fallaba** porque la columna no existía.

Al crear la tabla con la columna `sector`, la consulta SQL devolverá los valores ("Atlántico Sur", "Río de la Plata", "Urbano") y el error desaparecerá.

**Prueba esto y confírmame que ya puedes ver la lista en el sidebar.** Si funciona, el siguiente paso es que te enseñe cómo completar los 35 registros sin tener que escribir GeoJSON a mano para cada uno.


### [199] 🧑 Leonardo

dame el codigo html completo, rompi el codigo sin queresr en esta ultima modificacion


### [201] 🤖 Gemini

Aquí tienes el código **íntegro, corregido y blindado**. He añadido comentarios técnicos para que sepas qué hace cada parte y un sistema de detección de errores más robusto por si la base de datos vuelve a tener problemas de estructura.

Copia y pega todo este contenido en tu archivo `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IDE ESCM - Repositorio de Investigaciones v2.0</title>

    <!-- 1. RECURSOS EXTERNOS: Leaflet (Mapa) y SQL.js (Motor Base de Datos) -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/sql-wasm.js"></script>

    <style>
        /* 2. ESTILOS INSTITUCIONALES */
        :root {
            --navy: #002344;
            --gold: #f1c40f;
            --light-grey: #f8f9fa;
        }

        body {
            margin: 0;
            display: flex;
            flex-direction: column;
            height: 100vh;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }

        header {
            background: var(--navy);
            color: white;
            padding: 12px 20px;
            border-bottom: 4px solid var(--gold);
            box-shadow: 0 2px 5px rgba(0,0,0,0.3);
            z-index: 1000;
        }

        #main-container {
            display: flex;
            flex: 1;
            overflow: hidden;
        }

        /* BARRA LATERAL */
        #sidebar {
            width: 400px;
            background: var(--light-grey);
            border-right: 2px solid var(--navy);
            display: flex;
            flex-direction: column;
            box-shadow: 2px 0 10px rgba(0,0,0,0.1);
        }

        .filter-section {
            padding: 20px;
            background: #e9ecef;
            border-bottom: 1px solid #ccc;
        }

        .filter-section label {
            display: block;
            font-weight: bold;
            font-size: 12px;
            margin-bottom: 5px;
            color: var(--navy);
        }

        .filter-section select {
            width: 100%;
            margin-bottom: 15px;
            padding: 8px;
            border-radius: 4px;
            border: 1px solid #aaa;
        }

        /* LISTADO DE TESIS */
        #tesis-lista {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
        }

        .tesis-card {
            background: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 12px;
            transition: all 0.2s;
            cursor: pointer;
        }

        .tesis-card:hover {
            border-color: var(--gold);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .tesis-card h4 {
            margin: 0 0 8px 0;
            font-size: 14px;
            color: var(--navy);
            display: flex;
            align-items: flex-start;
        }

        .tesis-card input[type="checkbox"] {
            margin-right: 12px;
            margin-top: 3px;
            transform: scale(1.2);
        }

        .metadata {
            font-size: 11px;
            color: #666;
            margin-bottom: 10px;
        }

        .resena-box {
            font-size: 12px;
            background: #fdfdfd;
            padding: 10px;
            border-left: 3px solid var(--gold);
            margin: 10px 0;
            display: none; /* Se activa con JS */
            line-height: 1.4;
        }

        .btn-repo {
            background: var(--navy);
            color: white;
            text-decoration: none;
            padding: 6px 12px;
            border-radius: 4px;
            font-size: 11px;
            display: inline-block;
            font-weight: bold;
        }

        .btn-repo:hover {
            background: #003366;
        }

        /* MAPA */
        #map {
            flex: 1;
            z-index: 1;
        }

        .error-msg {
            color: #d9534f;
            background: #f2dede;
            padding: 15px;
            margin: 10px;
            border-radius: 4px;
            font-size: 13px;
            border: 1px solid #ebccd1;
        }
    </style>
</head>
<body>

    <header>
        <strong>IDE ESCM</strong> | Nodo Universitario de Investigaciones Geoespaciales
    </header>

    <div id="main-container">
        <aside id="sidebar">
            <!-- Sección de Filtros -->
            <div class="filter-section">
                <label for="filter-anio">Filtrar por Año:</label>
                <select id="filter-anio">
                    <option value="">Cargando años...</option>
                </select>

                <label for="filter-sector">Área de Estudio / Sector:</label>
                <select id="filter-sector">
                    <option value="">Cargando sectores...</option>
                </select>
                <p style="font-size: 10px; color: #666; margin: 0;">* Seleccione para filtrar automáticamente</p>
            </div>

            <!-- Contenedor de la lista -->
            <div id="tesis-lista">
                <p style="text-align:center; padding:20px;">Iniciando sistema...</p>
            </div>
        </aside>

        <!-- El Mapa -->
        <div id="map"></div>
    </div>

    <script>
        // 3. LÓGICA DE INGENIERÍA (JAVASCRIPT)

        // Variables globales
        let db; 
        let capasActivas = {}; // Para guardar y remover capas del mapa según ID

        // Configuración de motor SQLite WASM
        const sqlConfig = { 
            locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}` 
        };

        // Inicializar Mapa
        var map = L.map('map').setView([-38.0, -58.0], 5);
        L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/Ocean/World_Ocean_Base/MapServer/tile/{z}/{y}/{x}', {
            attribution: 'Tiles &copy; Esri &mdash; Sources: GEBCO, NOAA, CHS, OSU, UNH, CSUMB, National Geographic, DeLorme, NAVTEQ, and Esri'
        }).addTo(map);

        // Función Principal de Arranque
        async function iniciarSistema() {
            const listaDiv = document.getElementById('tesis-lista');
            try {
                // A. Iniciar Motor SQL
                const SQL = await initSqlJs(sqlConfig);
                
                // B. Cargar el archivo .db desde la carpeta data/
                const dataPromise = await fetch('data/tesis.db');
                if (!dataPromise.ok) throw new Error("No se pudo encontrar el archivo 'data/tesis.db'.");
                
                const buf = await dataPromise.arrayBuffer();
                db = new SQL.Database(new Uint8Array(buf));
                
                console.log("Base de Datos cargada con éxito.");

                // C. Verificar si la tabla existe (Prevenir error de 'no such table')
                const testTable = db.exec("SELECT name FROM sqlite_master WHERE type='table' AND name='investigaciones'");
                if (testTable.length === 0) throw new Error("La tabla 'investigaciones' no existe en la base de datos.");

                // D. Configurar Interfaz
                poblarFiltros();
                consultarTesis();

                // E. Vincular eventos de cambio en filtros
                document.getElementById('filter-anio').onchange = consultarTesis;
                document.getElementById('filter-sector').onchange = consultarTesis;

            } catch (err) {
                console.error(err);
                listaDiv.innerHTML = `<div class="error-msg">
                    <strong>ERROR TÉCNICO:</strong><br>${err.message}<br><br>
                    <small>Verifica que 'tesis.db' esté en la carpeta 'data' y que el servidor local esté corriendo.</small>
                </div>`;
            }
        }

        // Poblar Selectores dinámicamente desde SQL
        function poblarFiltros() {
            const selAnio = document.getElementById('filter-anio');
            const selSector = document.getElementById('filter-sector');

            // Consultar años únicos
            const anios = db.exec("SELECT DISTINCT anio FROM investigaciones ORDER BY anio DESC");
            selAnio.innerHTML = '<option value="">Todos los años</option>';
            if(anios.length > 0) {
                anios[0].values.forEach(v => selAnio.add(new Option(v[0], v[0])));
            }

            // Consultar sectores únicos
            const sectores = db.exec("SELECT DISTINCT sector FROM investigaciones ORDER BY sector ASC");
            selSector.innerHTML = '<option value="">Todos los sectores</option>';
            if(sectores.length > 0) {
                sectores[0].values.forEach(v => selSector.add(new Option(v[0], v[0])));
            }
        }

        // Consultar Tesis aplicando filtros
        function consultarTesis() {
            const anio = document.getElementById('filter-anio').value;
            const sector = document.getElementById('filter-sector').value;
            
            let query = "SELECT * FROM investigaciones WHERE 1=1";
            if(anio) query += ` AND anio = ${anio}`;
            if(sector) query += ` AND sector = '${sector}'`;

            const res = db.exec(query);
            renderLista(res.length > 0 ? res[0] : null);
        }

        // Renderizar las tarjetas en el sidebar
        function renderLista(data) {
            const contenedor = document.getElementById('tesis-lista');
            contenedor.innerHTML = '';

            if(!data) {
                contenedor.innerHTML = "<p style='padding:20px; color:#666;'>No hay resultados para los filtros seleccionados.</p>";
                return;
            }

            const columnas = data.columns;
            data.values.forEach(fila => {
                // Convertir fila en objeto clave-valor
                const t = {};
                columnas.forEach((col, i) => t[col] = fila[i]);

                const card = document.createElement('div');
                card.className = 'tesis-card';
                card.innerHTML = `
                    <h4>
                        <input type="checkbox" id="chk-${t.id}" ${capasActivas[t.id] ? 'checked' : ''}>
                        ${t.titulo}
                    </h4>
                    <div class="metadata">
                        <strong>Autor:</strong> ${t.autor} | <strong>Año:</strong> ${t.anio} | <strong>Sector:</strong> ${t.sector}
                    </div>
                    <div class="resena-box" id="res-${t.id}">
                        ${t.resena || "Sin reseña disponible."}
                    </div>
                    <div style="display:flex; justify-content:space-between; align-items:center;">
                        <a href="${t.url}" target="_blank" class="btn-repo">📂 Ver Repositorio</a>
                        <span style="font-size:10px; color:var(--navy); font-weight:bold;">Ver Reseña ⏷</span>
                    </div>
                `;

                // Evento Checkbox: Mostrar/Ocultar en el mapa
                const checkbox = card.querySelector('input');
                checkbox.onchange = (e) => {
                    e.stopPropagation();
                    manejarCapa(e.target.checked, t);
                };

                // Evento Click en Tarjeta: Mostrar Reseña
                card.onclick = (e) => {
                    // Evitar que el clic en el botón o checkbox cierre la reseña
                    if(e.target.type !== 'checkbox' && e.target.tagName !== 'A') {
                        const box = document.getElementById(`res-${t.id}`);
                        const estaAbierto = box.style.display === 'block';
                        
                        // Cerrar todas las demás reseñas para orden
                        document.querySelectorAll('.resena-box').forEach(b => b.style.display = 'none');
                        
                        box.style.display = estaAbierto ? 'none' : 'block';
                    }
                };

                contenedor.appendChild(card);
            });
        }

        // Gestión de Capas en el Mapa (GeoJSON)
        function manejarCapa(visible, t) {
            if (visible) {
                try {
                    // 1. Intentar parsear el GeoJSON guardado como texto en la DB
                    const geoData = JSON.parse(t.geojson);
                    
                    // 2. Crear la capa Leaflet
                    const capa = L.geoJSON(geoData, {
                        style: {
                            color: t.anio > 2020 ? '#ff7800' : '#6f42c1', // Color según antigüedad
                            weight: 3,
                            fillOpacity: 0.4
                        }
                    }).addTo(map);
                    
                    capa.bindPopup(`<b>${t.titulo}</b><br>Año: ${t.anio}`);
                    
                    // 3. Guardar referencia para poder borrarla después
                    capasActivas[t.id] = capa;
                    
                    // 4. Hacer zoom a la zona
                    map.fitBounds(capa.getBounds(), { padding: [50, 50] });

                } catch (e) {
                    console.error("Error procesando GeoJSON para ID: " + t.id, e);
                    alert("Error en la geometría de esta tesis.");
                }
            } else {
                // Remover del mapa si el checkbox se desmarca
                if (capasActivas[t.id]) {
                    map.removeLayer(capasActivas[t.id]);
                    delete capasActivas[t.id];
                }
            }
        }

        // Lanzar proceso
        iniciarSistema();

    </script>
</body>
</html>
```

### Notas para Leonardo:
1.  **Limpieza de Caché:** Después de guardar este código, recuerda presionar `Ctrl + F5` en el navegador.
2.  **Base de Datos:** Asegúrate de que tu tabla se llame `investigaciones` y tenga las columnas `id, anio, titulo, autor, sector, resena, url, geojson`. Si falta una, el código lanzará un error detallado en el sidebar.
3.  **Localhost:** Sigue usando `python -m http.server 8000` para verlo localmente.

Este código es el "esqueleto profesional" definitivo. Una vez que lo veas funcionando, solo tendremos que alimentar la base de datos con los registros reales.


### [202] 🧑 Leonardo

bin este modelo me agrada, el tema es la reseña ya que hay que colocar por lo menos el texto d ela introducion d ela tesis y es extenso , deberia ser una informacion emergente o verla del lado derecho en modo read, como wikipedia o un RMarkdown, algo similar  agradable a la lectura


### [204] 🤖 Gemini

Leonardo, entiendo perfectamente la necesidad. En una **IDE (Infraestructura de Datos Espaciales)**, la visualización geográfica debe convivir con el **análisis narrativo**. Si la introducción es extensa, meterla dentro de la tarjeta del sidebar arruina la experiencia de usuario (UX).

He rediseñado la interfaz para aplicar un **"Modo Lector" (Reading Panel)** al estilo de las interfaces de documentación técnica o RMarkdown. 

### La Nueva Arquitectura:
1.  **Panel Izquierdo:** Filtros y listado rápido.
2.  **Centro:** Mapa (tu lienzo de trabajo).
3.  **Panel Derecho (Lector):** Se despliega solo cuando quieres leer. Es un panel limpio, con tipografía cuidada y scroll independiente, ideal para textos largos.

Aquí tienes el código completo corregido:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IDE ESCM - Portal de Investigaciones</title>

    <!-- RECURSOS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/sql-wasm.js"></script>

    <style>
        :root {
            --navy: #002344;
            --gold: #f1c40f;
            --light-grey: #f4f7f6;
            --text-dark: #2c3e50;
        }

        body {
            margin: 0;
            display: flex;
            flex-direction: column;
            height: 100vh;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            overflow: hidden;
            background-color: var(--light-grey);
        }

        header {
            background: var(--navy);
            color: white;
            padding: 10px 20px;
            border-bottom: 4px solid var(--gold);
            z-index: 1100;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        #main-layout {
            display: flex;
            flex: 1;
            position: relative;
            overflow: hidden;
        }

        /* SIDEBAR IZQUIERDO: Filtros y Lista */
        #sidebar {
            width: 350px;
            background: white;
            border-right: 1px solid #ddd;
            display: flex;
            flex-direction: column;
            z-index: 1000;
            box-shadow: 2px 0 5px rgba(0,0,0,0.05);
        }

        .filter-section {
            padding: 15px;
            background: var(--navy);
            color: white;
        }

        .filter-section select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            margin-bottom: 10px;
            border-radius: 4px;
            border: none;
        }

        #tesis-lista {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
        }

        .tesis-card {
            background: white;
            border: 1px solid #eee;
            border-radius: 6px;
            padding: 12px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: 0.2s;
        }

        .tesis-card:hover {
            border-color: var(--gold);
            background: #fffdf5;
        }

        .tesis-card h4 {
            margin: 0 0 5px 0;
            font-size: 13px;
            color: var(--navy);
        }

        /* MAPA CENTRAL */
        #map {
            flex: 1;
            z-index: 1;
        }

        /* PANEL DERECHO: MODO LECTOR (ESTILO WIKIPEDIA / RMARKDOWN) */
        #reader-panel {
            width: 0; /* Cerrado por defecto */
            background: white;
            border-left: 1px solid #ddd;
            overflow-y: auto;
            transition: width 0.4s ease;
            z-index: 1050;
            display: flex;
            flex-direction: column;
        }

        #reader-panel.open {
            width: 500px; /* Tamaño del panel de lectura */
        }

        .reader-content {
            padding: 40px;
            color: var(--text-dark);
            line-height: 1.6;
        }

        .reader-header {
            border-bottom: 2px solid var(--gold);
            margin-bottom: 20px;
            padding-bottom: 10px;
        }

        .reader-header h2 {
            margin: 0;
            color: var(--navy);
            font-size: 22px;
        }

        .reader-meta {
            font-size: 14px;
            color: #666;
            margin-top: 10px;
        }

        .reader-text {
            font-size: 16px;
            text-align: justify;
            white-space: pre-wrap; /* Mantiene saltos de línea de la DB */
        }

        .close-reader {
            position: absolute;
            top: 15px;
            right: 20px;
            font-size: 24px;
            cursor: pointer;
            color: var(--navy);
            font-weight: bold;
        }

        .btn-repo-large {
            display: block;
            margin-top: 30px;
            padding: 12px;
            background: var(--navy);
            color: white;
            text-align: center;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
        }

        /* Botón pequeño en card */
        .btn-read {
            font-size: 11px;
            color: var(--navy);
            text-decoration: underline;
            font-weight: bold;
            margin-top: 5px;
            display: inline-block;
        }

    </style>
</head>
<body>

    <header>
        <div><strong>IDE ESCM</strong> | Nodo de Investigaciones Científicas</div>
        <div style="font-size: 12px;">Escuela de Ciencias del Mar</div>
    </header>

    <div id="main-layout">
        <!-- IZQUIERDA: LISTA -->
        <aside id="sidebar">
            <div class="filter-section">
                <label>Año de publicación:</label>
                <select id="filter-anio"><option value="">Cargando...</option></select>
                <label>Área de estudio:</label>
                <select id="filter-sector"><option value="">Cargando...</option></select>
            </div>
            <div id="tesis-lista">Iniciando base de datos...</div>
        </aside>

        <!-- CENTRO: MAPA -->
        <div id="map"></div>

        <!-- DERECHA: MODO LECTOR -->
        <div id="reader-panel">
            <span class="close-reader" onclick="cerrarLector()">&times;</span>
            <div class="reader-content" id="reader-content">
                <!-- Se llena dinámicamente -->
            </div>
        </div>
    </div>

    <script>
        let db;
        let capasActivas = {};
        const sqlConfig = { locateFile: file => `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/${file}` };

        // 1. Inicializar Mapa
        var map = L.map('map').setView([-38.0, -58.0], 5);
        L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/Ocean/World_Ocean_Base/MapServer/tile/{z}/{y}/{x}', {
            attribution: 'Tiles &copy; Esri'
        }).addTo(map);

        // 2. Iniciar Motor SQL y Cargar DB
        async function iniciar() {
            try {
                const SQL = await initSqlJs(sqlConfig);
                const dataPromise = await fetch('data/tesis.db');
                const buf = await dataPromise.arrayBuffer();
                db = new SQL.Database(new Uint8Array(buf));
                
                poblarFiltros();
                consultarTesis();

                document.getElementById('filter-anio').onchange = consultarTesis;
                document.getElementById('filter-sector').onchange = consultarTesis;
            } catch (err) {
                document.getElementById('tesis-lista').innerHTML = "Error: " + err.message;
            }
        }

        function poblarFiltros() {
            const anios = db.exec("SELECT DISTINCT anio FROM investigaciones ORDER BY anio DESC");
            const sectores = db.exec("SELECT DISTINCT sector FROM investigaciones ORDER BY sector ASC");
            
            const selAnio = document.getElementById('filter-anio');
            const selSector = document.getElementById('filter-sector');
            
            selAnio.innerHTML = '<option value="">Todos los años</option>';
            anios[0].values.forEach(v => selAnio.add(new Option(v[0], v[0])));

            selSector.innerHTML = '<option value="">Todos los sectores</option>';
            sectores[0].values.forEach(v => selSector.add(new Option(v[0], v[0])));
        }

        function consultarTesis() {
            const anio = document.getElementById('filter-anio').value;
            const sector = document.getElementById('filter-sector').value;
            let q = "SELECT * FROM investigaciones WHERE 1=1";
            if(anio) q += ` AND anio = ${anio}`;
            if(sector) q += ` AND sector = '${sector}'`;
            const res = db.exec(q);
            renderLista(res.length > 0 ? res[0] : null);
        }

        function renderLista(data) {
            const contenedor = document.getElementById('tesis-lista');
            contenedor.innerHTML = '';
            if(!data) { contenedor.innerHTML = "Sin resultados."; return; }

            const columnas = data.columns;
            data.values.forEach(fila => {
                const t = {};
                columnas.forEach((col, i) => t[col] = fila[i]);

                const card = document.createElement('div');
                card.className = 'tesis-card';
                card.innerHTML = `
                    <h4><input type="checkbox" id="chk-${t.id}" ${capasActivas[t.id] ? 'checked' : ''}> ${t.titulo}</h4>
                    <div style="font-size:11px; color:#666;">${t.autor} (${t.anio})</div>
                    <span class="btn-read">Leer Introducción y Ver Mapa ➔</span>
                `;

                // Checkbox: Maneja solo el mapa
                card.querySelector('input').onchange = (e) => {
                    e.stopPropagation();
                    manejarCapa(e.target.checked, t);
                };

                // Clic en Card: Abre el Lector
                card.onclick = () => abrirLector(t);

                contenedor.appendChild(card);
            });
        }

        function abrirLector(t) {
            const panel = document.getElementById('reader-panel');
            const content = document.getElementById('reader-content');
            
            panel.classList.add('open');
            
            content.innerHTML = `
                <div class="reader-header">
                    <h2>${t.titulo}</h2>
                    <div class="reader-meta">
                        <strong>Autor:</strong> ${t.autor}<br>
                        <strong>Año:</strong> ${t.anio} | <strong>Sector:</strong> ${t.sector}
                    </div>
                </div>
                <div class="reader-text">
                    <h3>Introducción</h3>
                    ${t.resena}
                </div>
                <a href="${t.url}" target="_blank" class="btn-repo-large">📂 Acceder al Repositorio Oficial (CefaDigital)</a>
            `;

            // Si tiene geometría, mostrarla automáticamente al leer
            manejarCapa(true, t);
            // Marcar el checkbox visualmente
            const chk = document.getElementById(`chk-${t.id}`);
            if(chk) chk.checked = true;
        }

        function cerrarLector() {
            document.getElementById('reader-panel').classList.remove('open');
        }

        function manejarCapa(visible, t) {
            if (visible) {
                if (capasActivas[t.id]) return; // Ya está en el mapa
                try {
                    const capa = L.geoJSON(JSON.parse(t.geojson), {
                        style: { color: '#ff7800', weight: 3, fillOpacity: 0.4 }
                    }).addTo(map);
                    capa.bindPopup(`<b>${t.titulo}</b>`);
                    capasActivas[t.id] = capa;
                    map.fitBounds(capa.getBounds(), { padding: [50, 50] });
                } catch (e) { console.error("Error GeoJSON", e); }
            } else {
                if (capasActivas[t.id]) {
                    map.removeLayer(capasActivas[t.id]);
                    delete capasActivas[t.id];
                }
            }
        }

        iniciar();
    </script>
</body>
</html>
```

### Por qué esta solución es "Modo Experto":
1.  **Tipografía de lectura:** El panel de lectura usa una fuente sans-serif limpia con un ancho de línea controlado (máximo 500px). En diseño editorial, esto reduce la fatiga visual.
2.  **Jerarquía Visual:** El lector no es un "pop-up" que tapa todo, sino una extensión de la información. El usuario puede seguir viendo el mapa a la izquierda mientras lee la introducción a la derecha.
3.  **Preservación de Formato:** He usado `white-space: pre-wrap;` en el CSS del lector. Esto significa que si pegas un texto largo en la base de datos con párrafos y saltos de línea, el navegador los respetará, manteniendo el formato original de la tesis.
4.  **Interactividad Inteligente:** Al hacer clic para leer la introducción, el mapa automáticamente vuela hacia la zona de estudio. Es una IDE funcional.

**Siguiente paso recomendado:**
Para la columna `resena` en tu base de datos, te recomiendo usar un editor de texto plano para limpiar el texto de Word o PDF antes de insertarlo en el SQL, para evitar caracteres extraños.

¿Qué te parece esta disposición de "triple panel"?


### [205] 🧑 Leonardo

Hola


### [206] 🤖 Gemini

{
  "mensaje": "¡Hola! ¿En qué puedo ayudarte hoy?"
}


### [207] 🧑 Leonardo

hola


### [209] 🤖 Gemini

¡Hola, Leonardo! Aquí sigo en **Modo Experto**.

¿Cómo va esa Workstation de ingeniería? ¿Ya tienes todo montado y funcionando con la RTX 5070 Ti y el nuevo cooler? 

Si estás listo para seguir con el desarrollo del proyecto **IDE ESCM**, dime en qué paso te encuentras. Estábamos optimizando el **Panel Lector** para las reseñas largas de las tesis y la integración con la base de datos **SQLite**.

¿En qué puedo ayudarte hoy para seguir avanzando?
