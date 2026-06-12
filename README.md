# MediaVault

**Panel CEP para After Effects y Premiere Pro que centraliza tu biblioteca de medios, con preview, importación inteligente y acceso directo al timeline.**

*MediaVault by Animateoo*

---

## Descripción corta (para GitHub)

> **MediaVault** es un panel de extensión para **Adobe After Effects** y **Adobe Premiere Pro** que te permite vincular carpetas locales (SFX, música, B-roll, imágenes) y usarlas como biblioteca sin salir del programa. Previsualiza audio con forma de onda, arrastra o haz doble clic para importar, y opcionalmente copia los archivos dentro de la carpeta de tu proyecto para que todo quede organizado y sin enlaces rotos.

---

## Descripción larga

**MediaVault** es una biblioteca de medios integrada en tu flujo de edición. En lugar de abrir el Explorador de archivos cada vez que necesitas un sonido o un clip, vinculas una o varias carpetas y el panel las indexa automáticamente: audios, videos, imágenes, presets `.ffx` y más.

Desde el panel puedes **buscar**, **previsualizar** (con forma de onda en audio y scrubbing en video), marcar **favoritos** y **importar** al proyecto con un doble clic o arrastrando hacia el timeline.

Una de sus funciones clave es la **copia automática al proyecto**: al usar un archivo, MediaVault puede duplicarlo dentro de la carpeta donde guardaste tu `.aep` o `.prproj`, en subcarpetas `(Footage)/Audio`, `(Footage)/Footage`, `(Footage)/Images`, etc. Así el proyecto lleva consigo una copia local del media y no depende de rutas externas que puedan moverse o borrarse. Si el archivo ya existe con el mismo nombre y tamaño, no crea duplicados innecesarios.

En **Premiere Pro**, los imports van al bin **MediaVault** del panel de proyecto y, si lo tienes activado, se insertan en la secuencia activa en la posición del playhead. En **After Effects**, se importan al proyecto y se añaden a la composición activa como capa.

---

## Características

- Vincular múltiples carpetas como bibliotecas independientes
- Vista lista o cuadrícula con mini formas de onda (audio)
- Preview con volumen, scrubbing y barra redimensionable
- Doble clic o botón para importar / añadir al timeline
- Arrastrar fuera del panel → insertar en timeline (Premiere)
- Copia opcional a `(Footage)/` junto al archivo del proyecto
- Detección de duplicados (mismo archivo ya importado o ya en Footage)
- Favoritos, búsqueda, menú contextual y ajustes persistentes
- Compatible con **After Effects** y **Premiere Pro**

---

## Requisitos

| Requisito | Detalle |
|-----------|---------|
| Host | Adobe After Effects CC 2014+ o Premiere Pro CC 2015+ |
| Sistema | Windows o macOS |
| CEP | CSXS 9.0 (incluido en versiones recientes de Creative Cloud) |
| Proyecto | Debe estar **guardado** si quieres usar la copia a `(Footage)/` |

---

## Instalación

### 1. Clonar o descargar

```bash
git clone https://github.com/Animateoo/MediaVault.git
```

### 2. Copiar la carpeta del panel

Coloca la carpeta **`MediaVault`** (con su `CSXS/manifest.xml` dentro) en la ruta de extensiones CEP:

**Windows**

```
C:\Program Files (x86)\Common Files\Adobe\CEP\extensions\MediaVault
```

**macOS**

```
/Library/Application Support/Adobe/CEP/extensions/MediaVault
```

> También puedes usar la carpeta de usuario en macOS:  
> `~/Library/Application Support/Adobe/CEP/extensions/`

### 3. Activar el modo desarrollador CEP (si el panel no aparece)

**Windows** — crear o editar en el Registro:

```
HKEY_CURRENT_USER\Software\Adobe\CSXS.11
```

Valor DWORD: `PlayerDebugMode` = `1`  
(Ajusta `CSXS.11` según tu versión: `.10`, `.12`, etc.)

**macOS** — en Terminal:

```bash
defaults write com.adobe.CSXS.11 PlayerDebugMode 1
```

### 4. Reiniciar After Effects o Premiere Pro

Abre el panel desde:

**Ventana → Extensiones → MediaVault**

---

## Uso básico

### 1. Vincular una carpeta

- Pulsa **Vincular carpeta** o arrastra una carpeta al área de bienvenida.
- La carpeta aparece en el árbol lateral. MediaVault escanea audios, videos e imágenes.

### 2. Explorar y previsualizar

- Navega por carpetas en el árbol o usa la **búsqueda**.
- Clic en un archivo → preview en la barra inferior.
- En audio verás la forma de onda; en video puedes hacer scrub con el ratón.

### 3. Importar al proyecto

| Acción | Resultado |
|--------|-----------|
| **Doble clic** | Importa y (si está activo) añade al timeline / comp activa |
| **Botón + en preview** | Igual que doble clic |
| **Botón importar en preview** | Solo importa al proyecto, sin timeline |
| **Arrastrar fuera del panel** (Premiere) | Inserta en la secuencia activa |
| **Menú contextual** | Importar, timeline, favoritos, abrir carpeta, etc. |

### 4. Ajustes recomendados

En el icono de **Ajustes** (engranaje):

| Opción | Descripción |
|--------|-------------|
| **Copiar a carpeta del proyecto** | Duplica el media a `(Footage)/Audio`, `Footage`, `Images`… junto a tu `.aep`/`.prproj` |
| **Añadir a timeline** | Al usar un archivo, lo coloca en la secuencia/comp activa en el playhead |
| **Escanear subcarpetas** | Indexa también las carpetas dentro de cada biblioteca |
| **Preview al pasar el mouse** | Reproduce mini preview de video al hover |

---

## Cómo funciona la copia al proyecto

Cuando **Copiar a carpeta del proyecto** está activado (por defecto: sí):

1. MediaVault detecta la carpeta donde guardaste el proyecto abierto (`.aep` / `.prproj`).
2. Antes de importar, **copia** el archivo a:
   - `(Footage)/Audio` — WAV, MP3, AIFF, etc.
   - `(Footage)/Footage` — MP4, MOV, MKV, etc.
   - `(Footage)/Images` — PNG, JPG, PSD, etc.
   - `(Footage)/Other` — otros tipos
3. El host importa **desde esa copia local**, no desde la biblioteca original.

**Ventajas:** el proyecto es portable, no pierdes media si mueves la biblioteca, y todo queda junto al archivo del proyecto.

**Comportamiento inteligente:**

- Si el archivo **ya está dentro** de la carpeta del proyecto → no copia de nuevo.
- Si ya existe en `(Footage)/` con el **mismo nombre y tamaño** → reutiliza ese archivo (sin `_1`, `_2`).
- Si existe con otro tamaño → crea `nombre_1.ext`, `nombre_2.ext`, etc.
- Si desactivas la opción en Ajustes → importa directamente desde la ruta original de la biblioteca.

> **Importante:** guarda el proyecto al menos una vez antes de importar con copia activada. Si no está guardado, MediaVault pedirá que lo guardes primero.

---

## After Effects vs Premiere Pro

| Función | After Effects | Premiere Pro |
|---------|---------------|--------------|
| Importar al proyecto | ✓ | ✓ (bin **MediaVault**) |
| Añadir al timeline / comp | Capa en comp activa | Clip en secuencia activa (playhead) |
| Presets `.ffx` | ✓ (capa seleccionada) | No soportado |
| Arrastrar fuera del panel | Import / comp | Insertar en timeline |
| Anti-duplicados en proyecto | — | ✓ (detecta clip ya importado) |

---

## Estructura del proyecto

```
MediaVault/
├── CSXS/manifest.xml    # Manifest CEP
├── index.html           # UI del panel
├── jsx/host.jsx         # Lógica ExtendScript (AE + PPRO)
├── js/
│   ├── app.js           # Interfaz principal
│   ├── library.js       # Escaneo y ajustes
│   ├── project.js       # Copia a (Footage)/
│   ├── preview.js       # Preview y formas de onda
│   └── ...
└── css/app.css
```

La configuración del usuario se guarda en:

```
%APPDATA%\MediaVault\          (Windows)
~/Library/Application Support/MediaVault/   (macOS, vía AppData Roaming equivalente)
```

---

## Atajos y tips

- **Esc** — cierra preview, modales o ajustes
- **Doble clic** — importar + timeline (rápido)
- Marca **favoritos** con la estrella para filtrar solo lo que usas más
- Usa **Reescanear biblioteca** si añades archivos fuera del panel

---
## Autor

**MediaVault** — creado por **Animateoo**

Si te resulta útil, considera dejar una estrella en el repositorio.
