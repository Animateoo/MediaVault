# MediaVault

**Panel CEP para After Effects y Premiere Pro que centraliza tu biblioteca de medios, con preview, importación inteligente y acceso directo al timeline.**

*MediaVault by Animateoo · Autor: Mateo Crespo (Animateo)*

---

## Descripción corta (para GitHub)

> **MediaVault** es un panel de extensión para **Adobe After Effects** y **Adobe Premiere Pro** que te permite vincular carpetas locales (SFX, música, B-roll, imágenes) y usarlas como biblioteca sin salir del programa. Previsualiza audio con forma de onda, arrastra o haz doble clic para importar, y opcionalmente copia los archivos dentro de la carpeta de tu proyecto para que todo quede organizado y sin enlaces rotos.

---

## Descripción larga

**MediaVault** es una biblioteca de medios integrada en tu flujo de edición. En lugar de abrir el Explorador de archivos cada vez que necesitas un sonido o un clip, vinculas una o varias carpetas y el panel las indexa automáticamente: audios, videos, imágenes, presets `.ffx` y más.

Desde el panel puedes **buscar**, **previsualizar** (con forma de onda en audio y scrubbing en video), marcar **favoritos** y **importar** al proyecto con un doble clic o arrastrando hacia el timeline.

Una de sus funciones clave es la **copia automática al proyecto**: al usar un archivo, MediaVault puede duplicarlo dentro de la carpeta donde guardaste tu `.aep` o `.prproj`, en subcarpetas `(Footage)/Audios`, `(Footage)/Footage`, `(Footage)/Images`, etc. Así el proyecto lleva consigo una copia local del media y no depende de rutas externas que puedan moverse o borrarse. Si el archivo ya existe con el mismo nombre y tamaño, no crea duplicados innecesarios.

En **Premiere Pro**, los imports van al bin **MediaVault** del panel de proyecto y, si lo tienes activado, se insertan en la secuencia activa en la posición del playhead. En **After Effects**, se importan al proyecto y se añaden a la composición activa como capa.

---

## Características

- Vincular múltiples carpetas como bibliotecas independientes
- Vista lista o cuadrícula con tamaños **S / M / L / XL**
- Mini formas de onda estilo barras para audio
- Preview con volumen, scrubbing y barra redimensionable
- Doble clic o botón para importar / añadir al timeline
- Arrastrar fuera del panel → insertar en timeline (After Effects y Premiere)
- Copia opcional a `(Footage)/` junto al archivo del proyecto
- Detección de duplicados (mismo archivo ya importado o ya en Footage)
- Favoritos, búsqueda rápida, menú contextual y ajustes persistentes
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

### Opción A — ZXP (recomendada)

1. Descarga `MediaVault.zxp` desde este repositorio.
2. Instálalo con [Anastasiy's Extension Manager](https://install.anastasiy.com/) u otro instalador ZXP compatible.
3. Reinicia After Effects o Premiere Pro.
4. Abre el panel: **Ventana → Extensiones → MediaVault**.

### Opción B — Carpeta CEP (desarrollo)

1. Descarga `Codigo Fuente.zip` y descomprímelo.
2. Coloca la carpeta **`MediaVault`** (con `CSXS/manifest.xml` dentro) en:

**Windows**

```
C:\Program Files (x86)\Common Files\Adobe\CEP\extensions\MediaVault
```

**macOS**

```
/Library/Application Support/Adobe/CEP/extensions/MediaVault
```

3. Activa el modo desarrollador CEP si el panel no aparece (`PlayerDebugMode = 1`).
4. Reinicia After Effects o Premiere Pro.

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
| **Arrastrar fuera del panel** | Añade a la comp / secuencia activa |
| **Menú contextual** | Importar, timeline, favoritos, abrir carpeta, etc. |

### 4. Ajustes recomendados

| Opción | Descripción |
|--------|-------------|
| **Copiar a carpeta del proyecto** | Duplica el media a `(Footage)/Audios`, `Footage`, `Images`… junto a tu `.aep`/`.prproj` |
| **Añadir a timeline** | Al usar un archivo, lo coloca en la secuencia/comp activa en el playhead |
| **Escanear subcarpetas** | Indexa también las carpetas dentro de cada biblioteca |
| **Preview al pasar el mouse** | Reproduce mini preview de video al hover |

---

## Cómo funciona la copia al proyecto

Cuando **Copiar a carpeta del proyecto** está activado (por defecto: sí):

1. MediaVault detecta la carpeta donde guardaste el proyecto abierto (`.aep` / `.prproj`).
2. Antes de importar, **copia** el archivo a:
   - `(Footage)/Audios` — WAV, MP3, AIFF, etc.
   - `(Footage)/Footage` — MP4, MOV, MKV, etc.
   - `(Footage)/Images` — PNG, JPG, PSD, etc.
   - `(Footage)/Other` — otros tipos
3. El host importa **desde esa copia local**, no desde la biblioteca original.

**Comportamiento inteligente:**

- Si el archivo **ya está dentro** de la carpeta del proyecto → no copia de nuevo (salvo migración desde la carpeta legacy `Audio` hacia `Audios`).
- Si ya existe en `(Footage)/` con el **mismo nombre y tamaño** → reutiliza ese archivo.
- Si existe con otro tamaño → crea `nombre_1.ext`, `nombre_2.ext`, etc.
- Si desactivas la opción en Ajustes → importa directamente desde la ruta original de la biblioteca.

> **Importante:** guarda el proyecto al menos una vez antes de importar con copia activada.

---

## After Effects vs Premiere Pro

| Función | After Effects | Premiere Pro |
|---------|---------------|--------------|
| Importar al proyecto | Sí | Sí (bin **MediaVault**) |
| Añadir al timeline / comp | Capa en comp activa | Clip en secuencia activa (playhead) |
| Presets `.ffx` | Sí (capa seleccionada) | No soportado |
| Arrastrar fuera del panel | Añade a comp activa | Insertar en timeline |
| Anti-duplicados en proyecto | Sí | Sí |

---

## Descargas de este repositorio

Este repositorio publica **paquetes listos**, no el árbol completo como working copy abierta:

| Archivo | Contenido |
|---------|-----------|
| `MediaVault.zxp` | Instalador firmado del panel |
| `Codigo Fuente.zip` | Código fuente empaquetado para revisión / instalación CEP |
| `LICENSE` / `CUSTOM_LICENSE` | Condiciones de uso |

---

## Licencia y uso permitido

**MediaVault es gratuito para uso personal y comercial**, pero el código y el plugin **no se pueden vender ni redistribuir como producto propio**.

Está permitido:

- Usar el plugin en tus proyectos personales y de cliente
- Estudiar el código fuente
- Reportar errores y proponer mejoras al autor

No está permitido:

- Vender este plugin o versiones derivadas
- Redistribuir versiones modificadas como producto independiente
- Publicar forks comercializables sin autorización expresa
- Eliminar o alterar los créditos del autor original

Consulta `LICENSE` y `CUSTOM_LICENSE` en este repositorio.

Si encuentras una mejora o corrección, compártela con el autor para evaluar su inclusión en la versión oficial.

---

## Autor

**MediaVault** — creado por **Mateo Crespo (Animateo / Animateoo)**

Si te resulta útil, considera dejar una estrella en el repositorio.
