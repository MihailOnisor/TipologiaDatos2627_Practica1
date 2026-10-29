# Tecnologías en proyectos de electrónica certificados por OSHWA

Práctica 1 de M2.851 Tipología y ciclo de vida de los datos, curso 2026-2027.

El notebook descubre los enlaces del directorio de OSHWA, visita las fichas de los proyectos y extrae metadatos. Después añade variables derivadas sobre menciones de tecnologías y posibles componentes. La extracción principal utiliza HTML, sin la API de OSHWA.

## Integrantes

- Mihail Onisor Muresan (confirmar el orden oficial de los apellidos).
- Xènia (apellidos pendientes).

## Fuente y repositorio

- Fuente: https://certification.oshwa.org/list.html
- Repositorio: https://github.com/MihailOnisor/TipologiaDatos2627_Practica1
- DOI de Zenodo: pendiente de publicación. No existe un DOI verificado en la carpeta.

## Archivos

- `source/M2_851_Practica1_OSHWA_Tecnologias_scraper_v1.0.0.ipynb`: notebook con la configuración, navegación, extracción, variables derivadas y exportación.
- `dataset/oshwa_electronics_technologies_dataset_v1.csv`: CSV existente, con una muestra de 20 proyectos y 52 columnas.
- `requirements.txt`: versiones registradas del entorno original; incluye paquetes ajenos al scraper.
- `.gitignore`: exclusiones de entornos, cachés y configuración local.

El enunciado y el material bibliográfico se conservan fuera del repositorio, en `../Material_Practica1/`. Los documentos de preparación de la entrega están en `../Seguimiento_Practica1/`.

## Preparación del entorno

Desde la raíz del repositorio, en PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m pip install jupyter
.\.venv\Scripts\python.exe -m jupyter notebook source/M2_851_Practica1_OSHWA_Tecnologias_scraper_v1.0.0.ipynb
```

Jupyter se instala como herramienta para abrir el notebook. Estas instrucciones no equivalen a una verificación de instalación de todas las versiones del entorno original.

## Configuración y ejemplos

Los parámetros se editan en la celda «Configuración inicial de la práctica»; no son argumentos de línea de comandos.

| Parámetro | Función |
| --- | --- |
| `MAX_PROYECTOS = 20` | Prueba limitada a los primeros 20 proyectos seleccionados. |
| `MAX_PROYECTOS = None` | Procesa todos los proyectos que pasen el filtro. Es la configuración actualmente guardada. |
| `SOLO_ELECTRONICA = True` | Selecciona proyectos cuyo tipo principal sea `Electronics`. |
| `SOLO_ELECTRONICA = False` | Desactiva el filtro por tipo de proyecto. |
| `USER_AGENT` | Identificación enviada al servidor. |
| `TIMEOUT = 30` | Tiempo máximo de espera por petición, en segundos. |
| `ESPERA_MIN = 1.5`, `ESPERA_MAX = 3.0` | Intervalo de la pausa aleatoria entre peticiones. |

Ejemplo de prueba: establece `MAX_PROYECTOS = 20` y `SOLO_ELECTRONICA = True`, reinicia el kernel y ejecuta las celdas en orden.

Ejemplo completo: establece `MAX_PROYECTOS = None` y `SOLO_ELECTRONICA = True`, reinicia el kernel y ejecuta las celdas en orden. Revisa antes los permisos de acceso y los resultados de robots.txt.

La exportación guarda el CSV en `dataset/`, tanto si Jupyter se inicia en la raíz como si se inicia en `source/`. Ejecutarla sustituye el CSV de ese nombre. La disponibilidad y los cambios de la fuente pueden modificar los resultados de una nueva ejecución.

## Estado del dataset y publicación

El CSV existente es de una ejecución anterior: contiene 20 registros y una columna `author_email` que el extractor actual ya no genera. No se ha regenerado durante la organización de la carpeta. Antes de publicar hay que decidir el alcance final, revisar la exclusión de correos, comprobar la correspondencia entre código y CSV y justificar la licencia de redistribución.

Las variables `technology_mentions`, `candidate_components`, sus recuentos y los indicadores `usa_*` son derivadas. Detectan texto y no acreditan que se haya comprobado físicamente cada componente ni su presencia en una lista de materiales.

Pendiente: completar autores, publicar la versión definitiva en Zenodo e incorporar aquí su DOI. El enunciado exige repositorio privado en la rama `main` y acceso del profesor.
