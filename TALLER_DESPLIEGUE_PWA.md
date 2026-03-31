# TALLER – DESPLIEGUE DE APLICACIONES (PWA)

## Proyecto base

Aplicación: **Chat para Superhéroes**

Archivos relevantes ya existentes en el proyecto:

- `index.html` (referencia del manifest)
- `manifest.json` (configuración de la PWA)
- `sw.js` (service worker)

---

## 1) Investigación de keys para manifest PWA (clasificadas)

> Nota importante para el taller: algunas keys de tu enunciado (como permisos de dispositivo y varias de desarrollador) pertenecen a **Chrome Extensions Manifest** o a APIs Web, no al **Web App Manifest** estándar de PWA.

### a) Keys de metadatos

Sí aplican a PWA:

- `name`
- `short_name`
- `description`
- `lang`
- `dir`
- `categories`
- `icons` (incluyendo `purpose`)
- `screenshots`

### b) Keys de permisos

En PWA **no existe** una key general de permisos en el manifest como `permissions`.

Permisos reales en PWA se gestionan por:

- Llamadas JavaScript a APIs del navegador (Geolocation, Notifications, Camera, etc.)
- Políticas del navegador y contexto seguro `https`

Ejemplos que **NO aplican** en Web App Manifest:

- `permissions`
- `host_permissions`
- `optional_permissions`

### c) Keys de ventana (UI/comportamiento de app instalada)

Sí aplican a PWA:

- `display`
- `orientation`
- `theme_color`
- `background_color`
- `start_url`
- `scope`
- `id`

### d) Keys de desarrollador

En Web App Manifest estándar, **no existe** un bloque formal tipo `developer`/`author` obligatorio.

Alternativas recomendadas:

- Documentar autoría en `README.md`
- Metadatos en `<meta>` de `index.html`
- Usar `description` y `categories` en manifest para información de catálogo

### e) Otras keys útiles

- `shortcuts`
- `related_applications`
- `prefer_related_applications`

---

## 2) Ejemplo aplicado y validado en este proyecto

Se actualizó `manifest.json` con:

- Metadatos: `name`, `short_name`, `description`, `lang`, `dir`, `categories`
- Ventana: `id`, `start_url`, `scope`, `display`, `orientation`, `theme_color`, `background_color`
- Íconos: `icons` con `purpose`
- Catálogo: `screenshots`
- Otros: `shortcuts`, `related_applications`, `prefer_related_applications`

### Validación técnica mínima

- JSON válido sintácticamente
- Rutas de íconos apuntando a archivos existentes del proyecto

---

## 3) Evidencia solicitada (capturas) y causas de no aplicación

### Capturas que debes incluir en el informe final

1. **Application > Manifest (DevTools)** mostrando:
	- nombre
	- colores
	- display
	- orientation
	- íconos cargados
2. **Install prompt** o instalación de la PWA
3. **Pantalla de la app instalada** (modo standalone)
4. **Sección de screenshots del manifest** (si el navegador la muestra)

### Causas por las que algunas keys no se pueden aplicar

- `permissions` y similares no son válidas en Web App Manifest de PWA.
- Si se agregan esas keys, el navegador puede ignorarlas o advertir que no son reconocidas.
- Los permisos en PWA se piden en tiempo de ejecución desde JavaScript y dependen del navegador/HTTPS.

---

## ¿Qué modificar del código actual?

### Cambios obligatorios (ya aplicados)

1. `manifest.json`
	- Corregir `short-name` a `short_name`
	- Agregar keys de metadatos, ventana y otras compatibles

### Cambios opcionales recomendados

1. `sw.js`
	- Incluir `manifest.json` en `APP_SHELL` para disponibilidad offline
2. Reemplazar screenshots placeholder por imágenes reales:
	- `img/screenshot-mobile.png`
	- `img/screenshot-desktop.png`

---

## ¿Qué nuevas clases crear?

Para este taller de manifest **no necesitas crear clases CSS ni clases JavaScript nuevas**.

Solo si quieres cubrir evidencia de permisos en runtime (opcional) podrías agregar:

- Un módulo JS simple para solicitar permisos (`Notification.requestPermission()`, geolocalización, etc.)
- Botones en UI para disparar esas pruebas

Pero esto es adicional y no obligatorio para validar keys de manifest.

---

## Entrega sugerida (checklist)

- [x] `manifest.json` actualizado con keys válidas
- [ ] Capturas de evidencia en navegador
- [ ] Documento final con explicación de keys aplicadas
- [ ] Sección de keys no aplicables y su causa técnica

