<p align="center">
  <img src="assets/logo.png" alt="ViBox" width="260">
</p>

<p align="center"><b>Pantalla de inicio estilo Netflix para Google TV, Android TV y Fire TV. Sin anuncios.</b></p>

<p align="center">
  <a href="https://github.com/GuilleMos/ViBox-releases/releases/latest/download/ViBox.apk"><b>⬇ Descargar ViBox (última versión)</b></a>
</p>

---

## Qué es ViBox

ViBox sustituye la pantalla de inicio de tu tele por una portada a pantalla completa y filas de películas,
series, vídeos y apps, sin publicidad y sin servicios en segundo plano. Es ligera y arranca al instante
incluso en teles modestas.

ViBox no aloja ni distribuye contenido: muestra catálogos públicos y usa los complementos y servicios
que configura cada usuario.

## Funciones

- **Portada como Netflix**, con el tráiler que empieza solo a los pocos segundos (en español si pones tu clave de TMDB).
- **Reproducir con un clic**: ViBox elige la mejor fuente (tu idioma, lista para ver al momento y la mejor calidad que permitas).
- **Reproductor propio**: «Saltar intro» y «Saltar resumen», cuenta atrás para el siguiente episodio (que ya está preparado),
  audio y subtítulos con su sincronía, tamaño y estilo, velocidad y **modo noche**. Recuerda el idioma que eliges en cada serie.
- **Filas configurables**: Seguir viendo, Nuevos episodios, Próximamente, «Porque viste…», catálogos de Stremio y de tus
  complementos, listas (ViBox, Trakt y Stremio), YouTube, mix de filas y Mis apps.
- **Búsqueda global y por voz**: películas, series, tus complementos, YouTube y tus apps a la vez.
- **Perfiles** con avatar, PIN y perfil infantil. Cada perfil tiene su propio «Seguir viendo», sus listas y sus cuentas
  (o comparte las que quieras con otro perfil).
- **Cuenta de ViBox** (opcional): la misma experiencia en la TV y en la web, Real-Debrid / AllDebrid, Trakt, «Ver en la TV»
  desde el navegador y **el móvil como mando** (cruceta, reproducción, volumen, escribir y cola).
- **Mis apps** con baldosas a cuadro completo, **salvapantallas** con tus series y películas, y **actualizaciones automáticas**.

## Aparatos compatibles

| Aparato | Funciona | Botón Inicio → ViBox |
| --- | --- | --- |
| **Google TV** (Chromecast con Google TV, Xiaomi, TCL, Sony, Hisense, Philips…) | ✓ | Accesibilidad (sin ordenador) o ADB |
| **Android TV** (Xiaomi Mi Box / TV Stick, NVIDIA Shield, teles Android TV…) | ✓ | Elegir ViBox al pulsar Inicio, accesibilidad o ADB |
| **Fire TV** (Fire TV Stick, Cube, teles con Fire TV) | ✓ | Accesibilidad |
| **Cajas Android** genéricas y proyectores con Android 6 o superior | ✓ | Elegir ViBox al pulsar Inicio |
| Samsung (Tizen), LG (webOS), Apple TV | — | Usa la web de ViBox en el navegador |

Funciona con mando (cruceta + OK), en procesadores de 32 y 64 bits y no necesita los servicios de Google.

## Instalación rápida (sin ordenador ni comandos)

Todo con el mando, en Google TV, Android TV y Fire TV:

1. Instala **Downloader** desde la tienda de la tele (Google Play o la de Amazon).
2. Dale permiso a Downloader para **instalar apps desconocidas**. Es el primer permiso obligatorio.
3. Escribe en Downloader esta dirección e instala ViBox:
   `https://github.com/GuilleMos/ViBox-releases/releases/latest/download/ViBox.apk`
4. En ViBox, entra en *Ajustes → Pantalla de inicio → Activar «botón Inicio → ViBox»* y activa **ViBox: botón Inicio**.
   Es el segundo permiso obligatorio. Desde ahí, el botón Inicio del mando abre ViBox, también en Fire TV.

> Android obliga a dar estos dos permisos a mano por seguridad; ninguna app puede hacerlo sola.
> El ordenador (ADB) solo hace falta para extras, como desactivar del todo el inicio de Google TV para liberar memoria.

Abajo tienes los pasos detallados de cada aparato.

## Instalación

### Google TV y Android TV
1. Instala **Downloader** desde Google Play.
2. En *Ajustes → Apps → Acceso especial → Instalar apps desconocidas*, permite **Downloader**.
3. Abre Downloader, escribe esta dirección y pulsa *Ir*:
   `https://github.com/GuilleMos/ViBox-releases/releases/latest/download/ViBox.apk`
4. Instala y abre ViBox.

### Fire TV
1. Busca e instala **Downloader** en la tienda de Amazon.
2. *Ajustes → Mi Fire TV → Opciones para desarrolladores → Instalar apps desconocidas* → activa **Downloader**.
   (Si no ves *Opciones para desarrolladores*: *Mi Fire TV → Información* y pulsa 7 veces sobre el nombre del aparato.)
3. Abre Downloader, escribe la dirección de arriba, instala y abre ViBox.
4. Para que el botón Inicio abra ViBox, mira el apartado siguiente.

### Con un ordenador (ADB), en cualquiera de ellas
1. Activa *Opciones de desarrollo → Depuración USB / ADB*.
2. Descarga [Android SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools) y el APK de ViBox.
3. Dentro de la carpeta de platform-tools (en Mac usa `./adb`):
   ```
   adb connect IP_DE_TU_TELE
   adb install -r ViBox.apk
   ```

## Que el botón Inicio abra ViBox

### Sin ordenador (Google TV, Android TV y Fire TV)
1. En ViBox: *Ajustes → Pantalla de inicio → Activar «botón Inicio → ViBox»*.
2. En la lista de Accesibilidad, activa **ViBox: botón Inicio**.

Desde ese momento, al pulsar Inicio se abre ViBox. ViBox solo mira qué pantalla se abre; no lee lo que escribes
ni lo que ves. Puedes apagarlo cuando quieras en el mismo sitio.

### Con ADB en Google TV (el inicio de Google deja de cargarse y libera memoria)
**Abre ViBox al menos una vez antes de hacerlo.**
```
adb shell pm disable-user --user 0 com.google.android.apps.tv.launcherx
adb shell pm disable-user --user 0 com.google.android.tungsten.setupwraith
adb shell cmd package set-home-activity com.vibox.launcher/.MainActivity
```
> Hay que desactivar **los dos** paquetes. Si solo se desactiva el primero, la tele parece congelada al pulsar Inicio.

Para volver al inicio de Google TV:
```
adb shell pm enable com.google.android.apps.tv.launcherx
adb shell pm enable com.google.android.tungsten.setupwraith
```

En **Android TV** clásico y cajas Android suele bastar con pulsar Inicio y elegir ViBox → *Siempre*.

### Salvapantallas de ViBox
Elige *ViBox* en el salvapantallas del sistema o, con ADB:
```
adb shell settings put secure screensaver_components com.vibox.launcher/.ScreensaverService
```

## Primeros pasos

1. **Ajustes → Cuenta de ViBox**: vincula la tele con un código (opcional, para perfiles, debrid, Trakt, web y mando).
2. **Ajustes → Filas de Inicio**: ordena, oculta o crea filas. **Mis apps**: mantén OK sobre una app para tenerla a mano.
3. Opcional: clave gratuita de **TMDB** (títulos, sinopsis y tráileres en español y «Porque viste…»).

## Preguntas frecuentes

**¿Cómo actualizo?** ViBox avisa sola, o en *Ajustes → Actualizaciones*. La primera vez Android pedirá permitir
*Instalar apps desconocidas* para ViBox.

**¿Y la voz en Fire TV?** El micrófono del mando lo usa Alexa. En ViBox puedes buscar escribiendo, o desde el móvil con el mando de la web.

**¿Los perfiles comparten Trakt o el debrid?** Solo si tú quieres: cada perfil puede usar la misma cuenta que otro o una distinta.

---

<sub>ViBox es un proyecto personal sin relación con Netflix, Stremio, Google, Amazon ni YouTube. Todas las marcas pertenecen a sus propietarios.</sub>
