# Skin-Hair Device

Sitio web de orientación para el cuidado de la piel y el cabello. Permite explorar fichas informativas de productos y, con una cuenta, completar un cuestionario para filtrar las recomendaciones según las respuestas.

El proyecto es informativo: no vende productos, no muestra precios ni stock propios y no ofrece diagnósticos médicos. Los enlaces externos pueden cambiar y no garantizan disponibilidad ni la identidad de un vendedor.

## Funcionalidades

- Catálogo organizado por zonas del rostro, cuerpo y cabello.
- Cuestionario para personalizar la visualización del catálogo.
- Cuentas de usuario y almacenamiento de respuestas.
- Fichas con información, etiquetas y enlaces externos.
- Consejos informativos que aparecen mientras se navega.

El filtro es una orientación general; no garantiza que un producto sea adecuado para una persona ni reemplaza la consulta con un profesional.

## Tecnologías

- PHP 8.1 o posterior
- MySQL o MariaDB
- HTML, CSS y JavaScript
- Apache con soporte para `.htaccess`

PHP requiere las extensiones `pdo_mysql` y `mbstring`.

## Estructura del proyecto

```text
skin-hair-device/
├── index.html
├── .htaccess
├── HTML/       # Páginas del sitio
├── CSS/        # Hojas de estilo
├── FONT/       # Tipografías
├── IMG/        # Imágenes y favicon
├── JS/         # JavaScript
├── PHP/        # Conexión, catálogo y componentes PHP
├── BD/
│   └── base_completa.sql
├── docs/
│   └── manuales/
├── capturas/
├── .gitignore
├── LICENSE
└── README.md
```

## Instalación local con XAMPP

1. Copiá la carpeta del proyecto dentro de `htdocs`. Por ejemplo:

   ```text
   C:\xampp\htdocs\skin-hair-device
   ```

2. Iniciá Apache y MySQL desde el panel de XAMPP.
3. Abrí phpMyAdmin e importá `BD/base_completa.sql` para crear la base y cargar el catálogo.
4. Abrí el sitio en el navegador:

   ```text
   http://localhost/skin-hair-device/
   ```

El archivo SQL está pensado para una instalación nueva. Si ya existen tablas o datos, hacé un respaldo y revisá el contenido del script antes de importarlo.

## Configuración de la base de datos

La conexión se realiza desde `PHP/bootstrap.php`. El proyecto admite estas variables de entorno:

```text
DB_HOST
DB_PORT
DB_NAME
DB_USER
DB_PASSWORD
```

Para desarrollo local, el código contempla valores predeterminados de XAMPP. En un servidor publicado, configurá las credenciales mediante variables de entorno y no subas contraseñas al repositorio.

## Base de datos

`BD/base_completa.sql` contiene el script de instalación de la base y el catálogo del proyecto. Antes de compartirlo, revisá que no incluya cuentas, contraseñas ni información personal real.

Para agregar un producto, completá sus datos en la tabla `productos` y asociá las etiquetas correspondientes en `tags_productos`. Para que aparezca en zonas específicas, usá `secciones_productos`. La tabla `informacion_productos` permite registrar la fuente oficial y la fecha de revisión.

## Catálogo

El catálogo contiene 206 fichas únicas distribuidas en 17 secciones. Un mismo producto puede aparecer en más de una sección, por lo que los conteos por sección se superponen. Las imágenes de productos se cargan desde direcciones externas; si una imagen deja de estar disponible, el sitio muestra una alternativa.

Los datos comerciales, ingredientes, presentaciones y disponibilidad pueden cambiar. Consultá la fuente oficial enlazada en cada ficha cuando esté disponible.

## Consejos informativos

El sitio incluye consejos sobre cuidado de la piel y el cabello. Se muestran durante la navegación y el usuario puede pausarlos o cerrarlos. No son notificaciones del sistema ni aparecen cuando el navegador está cerrado.

Las fuentes incluyen materiales de la [American Academy of Dermatology](https://www.aad.org/), enlazados también desde los consejos correspondientes.

## Capturas y documentación

Las capturas del sitio se guardan en `capturas/`. Los informes y manuales se guardan en `docs/`; podés agregar allí el informe del proyecto y la carpeta `docs/manuales/` con los manuales de usuario y desarrollo.

## Licencia

El código de este proyecto se distribuye bajo la licencia indicada en `LICENSE`. Los nombres, marcas, imágenes y recursos de terceros pertenecen a sus respectivos titulares.