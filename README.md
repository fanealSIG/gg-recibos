# 📦 App Recibo de Unidades — G&G Constructores S.A.S.

**Versión:** 1.0.8 · **Plataforma:** Android + Web (PWA) · **Última actualización:** 01 de abril de 2026

---

## ¿Qué es esta app?

Aplicación móvil y web para inspectores de campo de **Grupo G&G Constructores S.A.S.** que permite capturar recibos de unidades con descripción, ubicación alfanumérica, coordenadas GPS y hasta 3 fotografías por registro. Genera informes profesionales en PDF, Word (.doc) y Excel con membrete corporativo y firma de gerencia.

Funciona en **Android** (APK instalable) y en cualquier **navegador de escritorio** (Chrome, Edge). No requiere instalación de servidores — los datos se guardan localmente en el dispositivo.

---

## 🚀 Funcionalidades implementadas

### Captura de datos en campo
- ✅ Formulario con descripción/detalle, ubicación alfanumérica
- ✅ Captura de coordenadas GPS con precisión en metros
- ✅ Lectura automática de GPS desde el EXIF de la foto (cámara nativa, Google Fotos)
- ✅ Hasta **3 fotografías por recibo** con vista previa en grilla 2 columnas
- ✅ Eliminación individual de fotos antes de guardar
- ✅ Compresión automática de fotos (Samsung S24: 20 MB → ~150 KB)
- ✅ Selector de app de cámara: cámara del celular, cámara del navegador o galería

### Persistencia y seguridad
- ✅ Login con usuarios y contraseñas (3 perfiles: gerencia + 2 inspectores)
- ✅ Sesión persistente con `localStorage` — no pide contraseña al cambiar de app
- ✅ Guardado automático en `localStorage` al cerrar, minimizar o cambiar de aplicación
- ✅ Guardado periódico automático cada 30 segundos como respaldo
- ✅ Numeración de recibos con contador independiente — nunca se repite aunque se borren registros

### Exportación de informes
- ✅ **PDF** — informe completo con membrete G&G, logo, fotos (2 por fila), coordenadas GPS, resumen estadístico y firma de gerencia. Compatible con Samsung Series S mediante Blob URL
- ✅ **Word (.doc)** — mismo diseño que el PDF, documento editable. Descarga mediante Blob con MIME `application/msword` (compatible Android y PC)
- ✅ **Excel (.xlsx)** — dos hojas: `Recibos` (numeración, descripción, GPS, fuente GPS, nombre de archivo de fotos como `pathname`) y `Resumen` del proyecto. Generado con SheetJS

### Interfaz
- ✅ Diseño responsive — funciona en celular y computador
- ✅ Modo dark en header con logo G&G corporativo
- ✅ Barra de estado con fecha, estado GPS, contador de registros y estado de guardado
- ✅ Notificaciones tipo toast para todas las acciones
- ✅ Lista de recibos con fotos en grilla, GPS con indicador de fuente (EXIF / manual)

### Infraestructura
- ✅ PWA (Progressive Web App) — instalable desde Chrome en Android
- ✅ Service Worker con caché offline (`/gg-recibos/sw.js`)
- ✅ Publicada en GitHub Pages: [https://fanealsig.github.io/gg-recibos/](https://fanealsig.github.io/gg-recibos/)
- ✅ APK generado con PWABuilder (Trusted Web Activity)
- ✅ Sin servidor — cero costo de infraestructura

---

## 👥 Usuarios del sistema

| Perfil | Usuario | Contraseña | Acceso |
|---|---|---|---|
| 👔 Gerencia | `gerencia` | `gg2026admin` | Administración completa |
| 👷 Inspector 1 | `inspector1` | `campo2026` | Captura de recibos en campo |
| 👷 Inspector 2 | `inspector2` | `campo2026` | Captura de recibos en campo |

---

## 📁 Estructura del repositorio

```
gg-recibos/
├── index.html        # App completa (HTML + CSS + JS en un solo archivo)
├── manifest.json     # Configuración PWA para instalación en Android
├── sw.js             # Service Worker para funcionamiento offline
├── icon-192.png      # Ícono de la app (192×192 px)
├── icon-512.png      # Ícono de la app (512×512 px)
└── README.md         # Este archivo
```

---

## ⚙️ Tecnologías utilizadas

| Componente | Tecnología |
|---|---|
| Frontend / App | HTML5 + CSS3 + JavaScript vanilla |
| Generación Excel | [SheetJS v0.18.5](https://sheetjs.com/) |
| Lectura GPS EXIF | [exifr v7.1.3](https://github.com/MikeKovarik/exifr) |
| Empaquetado Android | [PWABuilder](https://pwabuilder.com/) (TWA) |
| Hosting | GitHub Pages |
| Almacenamiento | `localStorage` del navegador |

---

## 📱 Instalación en Android

1. Descargar el archivo `Recibo de Unidades GyG.apk` compartido por el administrador
2. Abrir el APK desde la carpeta Descargas
3. Si aparece aviso de *fuente desconocida* → Configuración → Permitir → Instalar
4. La app aparece en el menú como **RU G&G**

**Actualización:** No requiere reinstalar el APK. Al abrir la app carga automáticamente la versión más reciente desde GitHub Pages.

---

## 🗺️ Hoja de ruta — próximas versiones

| Versión | Funcionalidad | Estado |
|---|---|---|
| v1.1 | Edición de recibos existentes | Planificado |
| v1.1 | Campo de proyecto por recibo | Planificado |
| v1.1 | Mapa con puntos GPS (Leaflet) | Planificado |
| v1.2 | Librerías SheetJS y exifr embebidas (100% offline) | Planificado |
| v2.0 | Base de datos en la nube (Supabase) | En diseño |
| v2.0 | Sincronización entre dispositivos | En diseño |
| v2.0 | Dashboard web para gerencia | En diseño |
| v2.0 | Notificaciones push | En diseño |
| v3.0 | App nativa Android (React Native o Java) | Futuro |

---

## 📋 Historial de cambios

### v1.0.8 — 01 de abril de 2026
- Word: MIME type definitivo `application/msword`, extensión `.doc`, descarga siempre por Blob (elimina `btoa` que fallaba con fotos grandes)
- Excel: columna `Archivos de foto` muestra el nombre original del archivo (`pathname`) de cada foto separado por ` | `; registros sin `pathname` muestran conteo como fallback

### v1.0.7 — 01 de abril de 2026
- Firma digital de gerencia eliminada del código fuente por seguridad

### v1.0.6 — 01 de abril de 2026
- Múltiples fotos por recibo (hasta 3), grilla 2×2 en formulario e informes
- Compresión automática de fotos (fix Samsung S24)
- Numeración de recibos con contador independiente (fix repetición al borrar)
- Eliminación de opción Timestamp Camera (no compatible con apertura directa desde PWA)

### v1.0.5
- Login con `localStorage` — sesión persiste al cambiar de app en Android
- Guardado automático cada 30 segundos + evento `pagehide`
- Word con mismo diseño que PDF (bloques por recibo con fotos grandes)
- PDF con Blob URL — fix impresión en Samsung Series S

### v1.0.4
- Selector de app de cámara (cámara nativa, navegador, galería)
- Lectura automática de GPS desde EXIF de la foto
- Badge verde "GPS extraído automáticamente de la foto"

### v1.0.3
- Login con pantalla de acceso y 3 usuarios
- Guardado automático al cerrar/minimizar

### v1.0.2
- Exportación Word (.doc) y Excel (.xlsx)
- Exportación PDF con Blob URL para compatibilidad Android

### v1.0.1 — PMV
- Captura de recibos con GPS, foto, descripción y ubicación alfanumérica
- Exportación PDF con membrete G&G, logo y firma de gerencia
- Persistencia con localStorage

---

## 📞 Soporte

**Grupo G&G Constructores S.A.S.**
- 📱 312 728 13 72
- 📧 gerencia@grupogygconstructores.com

El soporte técnico, correcciones y actualizaciones tienen un valor de **$250.000 COP / mes**.
