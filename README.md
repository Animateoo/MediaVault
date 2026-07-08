# MediaVault

**Panel CEP para After Effects y Premiere Pro que centraliza tu biblioteca de medios, con preview, importaciÃ³n inteligente y acceso directo al timeline.**

*MediaVault by Animateoo*

---

## DescripciÃ³n corta (para GitHub)

> **MediaVault** es un panel de extensiÃ³n para **Adobe After Effects** y **Adobe Premiere Pro** que te permite vincular carpetas locales (SFX, mÃºsica, B-roll, imÃ¡genes) y usarlas como biblioteca sin salir del programa. Previsualiza audio con forma de onda, arrastra o haz doble clic para importar, y opcionalmente copia los archivos dentro de la carpeta de tu proyecto para que todo quede organizado y sin enlaces rotos.

---

## DescripciÃ³n larga

**MediaVault** es una biblioteca de medios integrada en tu flujo de ediciÃ³n. En lugar de abrir el Explorador de archivos cada vez que necesitas un sonido o un clip, vinculas una o varias carpetas y el panel las indexa automÃ¡ticamente: audios, videos, imÃ¡genes, presets `.ffx` y mÃ¡s.

Desde el panel puedes **buscar**, **previsualizar** (con forma de onda en audio y scrubbing en video), marcar **favoritos** y **importar** al proyecto con un doble clic o arrastrando hacia el timeline.

Una de sus funciones clave es la **copia automÃ¡tica al proyecto**: al usar un archivo, MediaVault puede duplicarlo dentro de la carpeta donde guardaste tu `.aep` o `.prproj`, en subcarpetas `(Footage)/Audio`, `(Footage)/Footage`, `(Footage)/Images`, etc. AsÃ­ el proyecto lleva consigo una copia local del media y no depende de rutas externas que puedan moverse o borrarse. Si el archivo ya existe con el mismo nombre y tamaÃ±o, no crea duplicados innecesarios.

En **Premiere Pro**, los imports van al bin **MediaVault** del panel de proyecto y, si lo tienes activado, se insertan en la secuencia activa en la posiciÃ³n del playhead. En **After Effects**, se importan al proyecto y se aÃ±aden a la composiciÃ³n activa como capa.

---

## CaracterÃ­sticas

- Vincular mÃºltiples carpetas como bibliotecas independientes
- Vista lista o cuadrÃ­cula con mini formas de onda (audio)
- Preview con volumen, scrubbing y barra redimensionable
- Doble clic o botÃ³n para importar / aÃ±adir al timeline
- Arrastrar fuera del panel â†’ insertar en timeline (After Effects y Premiere)
- Copia opcional a `(Footage)/` junto al archivo del proyecto
- DetecciÃ³n de duplicados (mismo archivo ya importado o ya en Footage)
- Favoritos, bÃºsqueda, menÃº contextual y ajustes persistentes
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

## InstalaciÃ³n

### 1. Clonar o descargar

```bash
git clone https://github.com/TU_USUARIO/MediaVault.git
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

> TambiÃ©n puedes usar la carpeta de usuario en macOS:  
> `~/Library/Application Support/Adobe/CEP/extensions/`

### 3. Activar el modo desarrollador CEP (si el panel no aparece)

**Windows** â€” crear o editar en el Registro:

```
HKEY_CURRENT_USER\Software\Adobe\CSXS.11
```

Valor DWORD: `PlayerDebugMode` = `1`  
(Ajusta `CSXS.11` segÃºn tu versiÃ³n: `.10`, `.12`, etc.)

**macOS** â€” en Terminal:

```bash
defaults write com.adobe.CSXS.11 PlayerDebugMode 1
```

### 4. Reiniciar After Effects o Premiere Pro

Abre el panel desde:

**Ventana â†’ Extensiones â†’ MediaVault**

---

## Uso bÃ¡sico

### 1. Vincular una carpeta

- Pulsa **Vincular carpeta** o arrastra una carpeta al Ã¡rea de bienvenida.
- La carpeta aparece en el Ã¡rbol lateral. MediaVault escanea audios, videos e imÃ¡genes.

### 2. Explorar y previsualizar

- Navega por carpetas en el Ã¡rbol o usa la **bÃºsqueda**.
- Clic en un archivo â†’ preview en la barra inferior.
- En audio verÃ¡s la forma de onda; en video puedes hacer scrub con el ratÃ³n.

### 3. Importar al proyecto

| AcciÃ³n | Resultado |
|--------|-----------|
| **Doble clic** | Importa y (si estÃ¡ activo) aÃ±ade al timeline / comp activa |
| **BotÃ³n + en preview** | Igual que doble clic |
| **BotÃ³n importar en preview** | Solo importa al proyecto, sin timeline |
| **Arrastrar fuera del panel** | AÃ±ade a la comp activa | Inserta en la secuencia activa |
| **MenÃº contextual** | Importar, timeline, favoritos, abrir carpeta, etc. |

### 4. Ajustes recomendados

En el icono de **Ajustes** (engranaje):

| OpciÃ³n | DescripciÃ³n |
|--------|-------------|
| **Copiar a carpeta del proyecto** | Duplica el media a `(Footage)/Audio`, `Footage`, `Images`â€¦ junto a tu `.aep`/`.prproj` |
| **AÃ±adir a timeline** | Al usar un archivo, lo coloca en la secuencia/comp activa en el playhead |
| **Escanear subcarpetas** | Indexa tambiÃ©n las carpetas dentro de cada biblioteca |
| **Preview al pasar el mouse** | Reproduce mini preview de video al hover |

---

## CÃ³mo funciona la copia al proyecto

Cuando **Copiar a carpeta del proyecto** estÃ¡ activado (por defecto: sÃ­):

1. MediaVault detecta la carpeta donde guardaste el proyecto abierto (`.aep` / `.prproj`).
2. Antes de importar, **copia** el archivo a:
   - `(Footage)/Audio` â€” WAV, MP3, AIFF, etc.
   - `(Footage)/Footage` â€” MP4, MOV, MKV, etc.
   - `(Footage)/Images` â€” PNG, JPG, PSD, etc.
   - `(Footage)/Other` â€” otros tipos
3. El host importa **desde esa copia local**, no desde la biblioteca original.

**Ventajas:** el proyecto es portable, no pierdes media si mueves la biblioteca, y todo queda junto al archivo del proyecto.

**Comportamiento inteligente:**

- Si el archivo **ya estÃ¡ dentro** de la carpeta del proyecto â†’ no copia de nuevo.
- Si ya existe en `(Footage)/` con el **mismo nombre y tamaÃ±o** â†’ reutiliza ese archivo (sin `_1`, `_2`).
- Si existe con otro tamaÃ±o â†’ crea `nombre_1.ext`, `nombre_2.ext`, etc.
- Si desactivas la opciÃ³n en Ajustes â†’ importa directamente desde la ruta original de la biblioteca.

> **Importante:** guarda el proyecto al menos una vez antes de importar con copia activada. Si no estÃ¡ guardado, MediaVault pedirÃ¡ que lo guardes primero.

---

## After Effects vs Premiere Pro

| FunciÃ³n | After Effects | Premiere Pro |
|---------|---------------|--------------|
| Importar al proyecto | âœ“ | âœ“ (bin **MediaVault**) |
| AÃ±adir al timeline / comp | Capa en comp activa | Clip en secuencia activa (playhead) |
| Presets `.ffx` | âœ“ (capa seleccionada) | No soportado |
| Arrastrar fuera del panel | AÃ±ade a comp activa | Insertar en timeline |
| Anti-duplicados en proyecto | âœ“ (detecta footage ya importado) | âœ“ (detecta clip ya importado) |

---

## Estructura del proyecto

```
MediaVault/
â”œâ”€â”€ CSXS/manifest.xml    # Manifest CEP
â”œâ”€â”€ index.html           # UI del panel
â”œâ”€â”€ jsx/host.jsx         # LÃ³gica ExtendScript (AE + PPRO)
â”œâ”€â”€ js/
â”‚   â”œâ”€â”€ app.js           # Interfaz principal
â”‚   â”œâ”€â”€ library.js       # Escaneo y ajustes
â”‚   â”œâ”€â”€ project.js       # Copia a (Footage)/
â”‚   â”œâ”€â”€ preview.js       # Preview y formas de onda
â”‚   â””â”€â”€ ...
â””â”€â”€ css/app.css
```

La configuraciÃ³n del usuario se guarda en:

```
%APPDATA%\MediaVault\          (Windows)
~/Library/Application Support/MediaVault/   (macOS, vÃ­a AppData Roaming equivalente)
```

---

## Atajos y tips

- **Esc** â€” cierra preview, modales o ajustes
- **Doble clic** â€” importar + timeline (rÃ¡pido)
- Marca **favoritos** con la estrella para filtrar solo lo que usas mÃ¡s
- Usa **Reescanear biblioteca** si aÃ±ades archivos fuera del panel

---

## Licencia

Consulta los archivos `LICENSE` (MIT) y `CUSTOM_LICENSE` incluidos en esta carpeta.

---

## Autor

**MediaVault** â€” creado por **Animateoo**

Si te resulta Ãºtil, considera dejar una estrella en el repositorio.

---


## Uso y Contribuciones

Este plugin es gratuito y ha sido desarrollado por Mateo Crespo (Animateo).

Puedes:

* Utilizar el plugin en proyectos personales y comerciales.
* Revisar y aprender del código fuente.
* Reportar errores y sugerir mejoras.
* Compartir optimizaciones, correcciones o nuevas funciones con el autor.

No está permitido:

* Vender este plugin o versiones derivadas del mismo.
* Redistribuir versiones modificadas como un producto independiente.
* Eliminar los créditos del autor original.
* Publicar versiones modificadas sin autorización previa.

Si realizas mejoras o correcciones, te agradecería que las compartieras para evaluarlas e incorporarlas a la versión oficial, beneficiando a toda la comunidad.

Autor: Mateo Crespo (Animateo)
