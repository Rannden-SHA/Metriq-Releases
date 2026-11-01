# Metriq 2.1.1

**Español** · [English](#english)

## Español

Revisión de la 2.1 centrada en la instalación: **los paquetes llevan su propio Python**, llega el
**manual de usuario en PDF** y las descargas pasan a este repositorio. Se instala encima de la 2.0.x
y de la 2.1.0 conservando datos, configuración, claves y licencia.

### Novedades

- **Ya no hace falta instalar Python.** Los instaladores de Windows y Linux traen su propio Python
  (CPython 3.12.15). Un Python que ya hubiera en el servidor no se usa ni se modifica.
- **Al actualizar desde la 2.0 o la 2.1.0**, el asistente rehace el entorno de Python con el Python
  incluido. Los datos, la licencia y la configuración no se tocan, y si algo falla se vuelve a la
  instalación anterior. Después puedes desinstalar el Python del sistema si no lo usa nada más.
- **Paquete Debian `metriq_2.1.1_amd64.deb`** (antes `metriq_<versión>_all.deb`), porque lleva un
  Python de 64 bits x86. Actualiza sin más una instalación hecha con `metriq_2.1.0_all.deb`:
  `sudo apt install ./metriq_2.1.1_amd64.deb` y después `sudo metriq-setup --upgrade`.
- **Manual de usuario en PDF**, en español y en inglés, accesible desde el Centro de ayuda, el menú
  lateral de Ayuda y la web.
- **Las descargas pasan a este repositorio.** La instalación en una línea descarga la última versión
  y comprueba su huella SHA-256 antes de ejecutarla:
  `curl -fsSL https://github.com/Rannden-SHA/Metriq-Releases/releases/latest/download/install.sh | sudo sh`
- Los instaladores ocupan menos: llevan la variante oficial de Python sin símbolos de depuración (en
  Linux, unos 124 MB menos instalado).
- Los instaladores ya no incluyen los archivos de origen del manual: el manual se descarga aparte,
  en PDF.

### Correcciones

**Instalación**

- Linux: la instalación en una línea (`curl … | sudo sh`) vuelve a funcionar en Ubuntu y Debian
  (tomaba la versión de la distribución por la de Metriq y no encontraba el paquete) y vuelve a abrir
  el asistente interactivo en la terminal.
- Linux: la cuenta de administrador se crea con la contraseña elegida en el asistente, y el fichero
  temporal con esa contraseña se borra en el primer arranque. Antes el inicio de sesión fallaba tras
  instalar como servicio.
- Los mensajes del instalador autoextraíble (`.run`) y de `install.sh` salen también en inglés.
- En una instalación en inglés, la tarea programada de copias («Metriq - Backup») y los accesos del
  menú Inicio («Uninstall Metriq», «Data folder») salen en inglés. Al actualizar se sustituyen los del
  idioma anterior y la desinstalación limpia los dos.
- Windows: ya no aparecen accesos «Desinstalar Metriq» duplicados ni una segunda entrada de Metriq en
  «Aplicaciones instaladas».

**Aplicación**

- Las fechas y horas de toda la API van siempre en UTC con zona: el catálogo de métricas ya no
  muestra «Actualizada dentro de 3 h» ni la «Última modificación» desplazada en zonas al oeste de UTC.
- La vista pública y la incrustada (`/public/…`, también con `?embed=1`) formatean importes, números y
  fechas con la moneda, el formato regional y la zona horaria de la organización (antes, siempre en
  euros).
- En inglés con formato regional en-US, las fechas salen al estilo estadounidense («Nov 1, 2026,
  2:05 PM», 12 h); el castellano no cambia.
- Seguridad de filas: el SQL nativo y las métricas con SQL solo se bloquean a quien le afecta alguna
  política de la fuente (las de «Todos los usuarios» o las de sus grupos). El aviso explica qué hacer:
  usar el editor visual o pedir acceso «Total».
- Administración › IA › Uso y Límites: las tablas ya no se salen de su tarjeta y los nombres y
  correos largos se recortan.
- Nuevo objetivo: el selector «Formato» ya no sale cortado y el formulario no se desplaza en
  horizontal.

### Ficheros

| Fichero | Para qué |
|---|---|
| **`MetriqSetup-2.1.1.exe`** | Instalador para Windows 10/11 y Windows Server 2016 o posterior (64 bits). Incluye Python y todas las dependencias: no necesita internet. |
| **`metriq-installer-2.1.1.run`** | Instalador autoextraíble para Linux x86-64, cualquier distribución con systemd. Opción recomendada en Linux: `sudo ./metriq-installer-2.1.1.run`. |
| `metriq-installer-2.1.1.run.sha256` | Huella SHA-256 del `.run`; la usa `install.sh`. |
| **`metriq_2.1.1_amd64.deb`** | Paquete para Debian y Ubuntu (amd64): `sudo apt install ./metriq_2.1.1_amd64.deb` y después `sudo metriq-setup`. |
| `metriq-2.1.1.tar.gz` | Paquete para instalación manual o para revisar el contenido: `tar xzf` y `sudo ./install.sh`. |
| `install.sh` | Instalación en una línea en Linux: descarga la última versión, comprueba su huella y abre el asistente. |
| `SHA256SUMS.txt` | Huellas SHA-256 de todos los ficheros de esta versión. |
| `Metriq-Manual-es.pdf` | Manual de usuario en español. |
| `Metriq-Manual-en.pdf` | Manual de usuario en inglés. |

### Huellas SHA-256

```
66de9b4ef7cec1e5e608d859fc964357f9ccc82ae6f91754fd98b033b2ea9308  MetriqSetup-2.1.1.exe
d56d7db1f811106484c5a199ecad531d1536892b877eb8846f05176caf5fbbe4  metriq-installer-2.1.1.run
24a599fa95a2de3ba5ed03aeb0fd9f3eb70b41fe61c4590fbc7b50c2c9da6eca  metriq-installer-2.1.1.run.sha256
fd8611fad9140522836f1d318649843883415cabcf7dafa6423855efe51015b8  metriq_2.1.1_amd64.deb
dcfad3e03208459955d3d0a552441e2aa0dd36f1f34c3d5c2c665f44fd434997  metriq-2.1.1.tar.gz
1923ea2563d39e749e8534f755bcdf3221f602a59e408a0ffe02d0b72f26eab0  install.sh
423ddfde874bb4b85ed0c133a7efaf270f398281c932881d94152787d7494dab  Metriq-Manual-es.pdf
f65d5d66203de0a3cdabb28bae3dac06343489a944c814b7e90d06606586f1af  Metriq-Manual-en.pdf
```

Compruébalas con `sha256sum -c --ignore-missing SHA256SUMS.txt` en Linux o con
`Get-FileHash .\MetriqSetup-2.1.1.exe -Algorithm SHA256` en PowerShell.

El instalador de Windows no está firmado digitalmente: Windows SmartScreen puede mostrar «Windows
protegió su PC»; pulsa «Más información» → «Ejecutar de todas formas» tras comprobar la huella.

Metriq es software propietario de NextCode Agency. Los paquetes incluyen el acuerdo de licencia de
usuario final de Metriq (`LICENSE`), que se muestra y se acepta al instalar.

Sin licencia, Metriq funciona con las funciones básicas; los módulos se activan con una licencia
firmada. Licencias: [info@nextcodeagency.com](mailto:info@nextcodeagency.com). Más información en
[nextcodeagency.com/proyectos/metriq](https://nextcodeagency.com/proyectos/metriq).

---

## English

Patch release of 2.1 focused on installation: **the packages ship their own Python**, the **user
manual in PDF** arrives and downloads move to this repository. It installs over 2.0.x and 2.1.0 and
keeps your data, configuration, keys and license.

### What's new

- **You no longer need to install Python.** The Windows and Linux installers ship their own Python
  (CPython 3.12.15). Any Python already on the server is neither used nor changed.
- **When you upgrade from 2.0 or 2.1.0**, the wizard rebuilds the Python environment with the bundled
  Python. Data, license and configuration are kept, and if anything fails the previous installation
  is restored. Afterwards you can uninstall the system Python if nothing else uses it.
- **Debian package `metriq_2.1.1_amd64.deb`** (previously `metriq_<version>_all.deb`), because it
  bundles an x86-64 Python. It upgrades an installation made with `metriq_2.1.0_all.deb` in place:
  `sudo apt install ./metriq_2.1.1_amd64.deb`, then `sudo metriq-setup --upgrade`.
- **User manual in PDF**, in English and Spanish, available from the Help center, the Help side menu
  and the website.
- **Downloads move to this repository.** The one-line install downloads the latest version and
  checks its SHA-256 hash before running it:
  `curl -fsSL https://github.com/Rannden-SHA/Metriq-Releases/releases/latest/download/install.sh | sudo sh`
- Smaller installers: they ship the official Python build without debug symbols (on Linux, about
  124 MB less once installed).
- The installers no longer include the manual's source files: the manual is a separate PDF download.

### Fixes

**Installation**

- Linux: the one-line install (`curl … | sudo sh`) works again on Ubuntu and Debian (it mistook the
  distribution's version for Metriq's and couldn't find the package) and opens the interactive wizard
  in the terminal again.
- Linux: the administrator account gets the password you choose in the setup wizard, and the
  temporary file holding that password is deleted on first start. Previously, signing in failed after
  installing as a service.
- Messages from the self-extracting installer (`.run`) and `install.sh` are now also available in
  English.
- In an English installation, the scheduled backup task ("Metriq - Backup") and the Start menu
  shortcuts ("Uninstall Metriq", "Data folder") are in English. An update replaces the ones in the
  previous language, and uninstalling removes both.
- Windows: no more duplicate "Uninstall Metriq" shortcuts and no second Metriq entry in Installed
  apps.

**Application**

- Every date and time in the API is sent in UTC with a time zone: the metric catalog no longer shows
  "Updated in 3 hours" or a shifted "Last modified" west of UTC.
- Public and embedded views (`/public/…`, including `?embed=1`) format amounts, numbers and dates with
  the organization's currency, regional format and time zone (previously always euros).
- In English with the en-US regional format, dates use US style ("Nov 1, 2026, 2:05 PM", 12-hour
  clock); Spanish is unchanged.
- Row-level security: native SQL and SQL-based metrics are only blocked for people a policy on the
  source applies to ("All users" policies or those for their groups). The message explains what to
  do: use the visual editor or ask for "Full" access.
- Administration › AI › Usage and Limits: tables no longer overflow their card, and long names and
  emails are truncated.
- New goal: the "Format" selector is no longer cut off and the form no longer scrolls sideways.

### Files

| File | What it's for |
|---|---|
| **`MetriqSetup-2.1.1.exe`** | Installer for Windows 10/11 and Windows Server 2016 or later (64-bit). Bundles Python and every dependency, so it needs no Internet access. |
| **`metriq-installer-2.1.1.run`** | Self-extracting installer for x86-64 Linux, any distribution with systemd. The recommended option on Linux: `sudo ./metriq-installer-2.1.1.run`. |
| `metriq-installer-2.1.1.run.sha256` | SHA-256 hash of the `.run`; used by `install.sh`. |
| **`metriq_2.1.1_amd64.deb`** | Package for Debian and Ubuntu (amd64): `sudo apt install ./metriq_2.1.1_amd64.deb`, then `sudo metriq-setup`. |
| `metriq-2.1.1.tar.gz` | Package for a manual install, or to review the contents: `tar xzf` and `sudo ./install.sh`. |
| `install.sh` | One-line Linux install: downloads the latest version, checks its hash and opens the wizard. |
| `SHA256SUMS.txt` | SHA-256 hashes of every file in this release. |
| `Metriq-Manual-en.pdf` | User manual in English. |
| `Metriq-Manual-es.pdf` | User manual in Spanish. |

### SHA-256 checksums

```
66de9b4ef7cec1e5e608d859fc964357f9ccc82ae6f91754fd98b033b2ea9308  MetriqSetup-2.1.1.exe
d56d7db1f811106484c5a199ecad531d1536892b877eb8846f05176caf5fbbe4  metriq-installer-2.1.1.run
24a599fa95a2de3ba5ed03aeb0fd9f3eb70b41fe61c4590fbc7b50c2c9da6eca  metriq-installer-2.1.1.run.sha256
fd8611fad9140522836f1d318649843883415cabcf7dafa6423855efe51015b8  metriq_2.1.1_amd64.deb
dcfad3e03208459955d3d0a552441e2aa0dd36f1f34c3d5c2c665f44fd434997  metriq-2.1.1.tar.gz
1923ea2563d39e749e8534f755bcdf3221f602a59e408a0ffe02d0b72f26eab0  install.sh
423ddfde874bb4b85ed0c133a7efaf270f398281c932881d94152787d7494dab  Metriq-Manual-es.pdf
f65d5d66203de0a3cdabb28bae3dac06343489a944c814b7e90d06606586f1af  Metriq-Manual-en.pdf
```

Check them with `sha256sum -c --ignore-missing SHA256SUMS.txt` on Linux or with
`Get-FileHash .\MetriqSetup-2.1.1.exe -Algorithm SHA256` in PowerShell.

The Windows installer is not code-signed: Windows SmartScreen may show "Windows protected your PC";
click "More info" → "Run anyway" after checking the hash.

Metriq is proprietary software owned by NextCode Agency. The packages include the Metriq end user
license agreement (`LICENSE`), which is shown and accepted during installation.

Without a license, Metriq runs with its core features; the modules are unlocked by a signed license.
Licensing: [info@nextcodeagency.com](mailto:info@nextcodeagency.com). More information at
[nextcodeagency.com/proyectos/metriq](https://nextcodeagency.com/proyectos/metriq).
