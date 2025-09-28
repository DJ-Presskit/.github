🔧 Flujo completo para armar un nuevo presskit
1) Preparación

Abrir el Google Sheet maestro de presskits.

Elegir el DJ asignado y marcarlo en estado EN DESARROLLO.

Copiar/ordenar los datos (opcional: usar IA para limpiar bio o textos).

2) Crear repositorio

Crear un nuevo repo usando el template de cápsula vigente (capsula-xx-template).

Nombrarlo según convención: nombreDJ-dj-presskit (camelCase).

Clonar el repo localmente.

Configurar variables de entorno (.env.local).

3) Google Sheets (gigs y data dinámica)

En Google Drive:

Ir a _PRESSKITS > Cápsula XX (nombre de la cápsula) > Carpeta DJ (ej. FacuArce-dj-presskit).

Crear carpeta propia del DJ.

Dentro, copiar el archivo base:
_DJ PRESSKITS WEBS > TEMPLATE > PRESSKIT.xlsx.

Renombrar el archivo a PRESSKIT.

Abrir el archivo en Google Sheets y copiar el ID de la URL (la parte entre /d/ y /edit).

Ejemplo:

https://docs.google.com/spreadsheets/d/1kPP8f3xSZchwUb6GmyshPHlRlugQVGdWqSlLbKBs_Fg/edit


→ ID: 1kPP8f3xSZchwUb6GmyshPHlRlugQVGdWqSlLbKBs_Fg

Pegar este ID en el .env.local bajo la variable:

GOOGLE_SHEET_ID=1kPP8f3xSZchwUb6GmyshPHlRlugQVGdWqSlLbKBs_Fg


Compartir la carpeta del DJ con el mail de servicio de Google (el que usamos para la API).

Eliminar filas/columnas vacías del template en el Sheet.

4) Carpeta PRESSKIT en Drive

En la carpeta del DJ crear subcarpeta PRESSKIT/.

Esa carpeta debe estar pública (acceso a link).

Copiar el URL y pegarlo en DATA.ts > DJINFO.driveUrl.

5) Conexión con SoundCloud (si aplica)

Entrar al SoundCloud API Explorer:
https://developers.soundcloud.com/docs/api/explorer/open-api#/search/get_users

Iniciar sesión en el candado 🔒 con las credenciales de la cuenta SoundCloud (guardadas en ENV).

En la query GET /users, borrar todos los params menos q.

Escribir el nombre del DJ y ejecutar la búsqueda.

Buscar en los resultados al DJ correcto (revisar varios si hay homónimos).

Copiar el valor de urn, ej:

soundcloud:users:798293017


Pegar ese valor en el .env.local en la variable correspondiente:

SOUNDCLOUD_USER_URN=soundcloud:users:798293017


Si los tracks no aparecen en local, borrar localStorage y cache del navegador.

6) Ajuste de contenidos

Completar y revisar toda la info enviada en el formulario del DJ.
Los archivos a actualizar son:

content/dj/DATA.ts → info estructurada del DJ (bio, links, gigs, rider, contactos).

content/i18n/es.json → textos en español.

content/i18n/en.json → traducción en inglés.
