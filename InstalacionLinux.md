**Instalación y Configuración de Linux I**

---

### 1. Introducción
Linux es un sistema operativo de código abierto desarrollado inicialmente por Linus Torvalds, basado en Unix. Su flexibilidad, seguridad y eficiencia han permitido su adopción en servidores, dispositivos embebidos, estaciones de trabajo y sistemas personales. Desde su versión 1.0, ha evolucionado hasta convertirse en uno de los sistemas operativos más utilizados en entornos empresariales y educativos.

---

### 2. Historia de Linux y su Relación con GNU

#### 2.1. Creación del Kernel de Linux
Linus Torvalds desarrolló el kernel de Linux en 1991 mientras estudiaba en la Universidad de Helsinki. Buscaba crear un sistema similar a UNIX que pudiera ejecutarse en hardware de consumo y que permitiera una mayor flexibilidad para el aprendizaje y la experimentación.

El **kernel** es el componente central de un sistema operativo que gestiona los recursos del hardware, incluyendo memoria, procesos y dispositivos. Se encarga de la comunicación entre el software y el hardware, garantizando la eficiencia en la administración de recursos.

#### 2.2. Rol del Proyecto GNU
GNU ("GNU is Not Unix") es un proyecto iniciado por Richard Stallman en 1983 con el objetivo de desarrollar un sistema operativo completamente libre. El kernel de Linux, desarrollado posteriormente, fue integrado con herramientas y programas del proyecto GNU, dando origen al sistema GNU/Linux. El Proyecto GNU proporcionó componentes esenciales como el compilador GCC, la biblioteca estándar (glibc) y herramientas de línea de comandos fundamentales.

#### 2.3. Distribuciones GNU/Linux
Algunas distribuciones populares y sus usos principales son:
- **Debian**: Enfocada en estabilidad y servidores.
- **Ubuntu**: Uso general y facilidad de instalación.
- **Fedora**: Desarrollo y entornos empresariales.
- **openSUSE**: Servidores y escritorios corporativos.
- **Arch Linux**: Personalización y minimalismo.

Cada distribución incluye un gestor de paquetes específico para facilitar la instalación y actualización del software.

---

### 3. Licencias de Software

#### 3.1. Cuatro libertades del Software Libre
La **GPL (General Public License)** establece cuatro libertades fundamentales:
1. **Libertad de uso**: Ejecutar el programa con cualquier propósito.
2. **Libertad de estudio**: Acceder al código fuente y modificarlo.
3. **Libertad de distribución**: Compartir copias del programa.
4. **Libertad de mejora**: Modificar y distribuir versiones mejoradas.

#### 3.2. Comparación GPL vs. Creative Commons
- **GPL**: Se aplica a software, garantizando el acceso al código fuente y protegiendo los derechos de modificación y distribución. Obliga a que cualquier software derivado mantenga la misma licencia.
- **Creative Commons**: Se usa para obras creativas (textos, imágenes, música) y permite diferentes niveles de acceso y distribución. No se aplica específicamente a software.

#### 3.3. Caso de Uso del Software Libre
Ejemplo: **Android**, basado en el kernel de Linux, ha permitido la creación de un ecosistema abierto de desarrollo móvil, fomentando la innovación y reduciendo costos. Empresas como Red Hat han construido modelos de negocio exitosos en torno al software libre.

---

### 4. Entornos Gráficos y X-Windows

#### 4.1. Definición de X-Windows
X-Windows (X11) es el sistema de gestión de ventanas en sistemas Unix y Linux. Permite la interacción gráfica con el sistema mediante entornos de escritorio como GNOME y KDE. 

#### 4.2. Comparación de GNOME, KDE y Xfce
- **GNOME**: Interfaz moderna, optimizada para accesibilidad y productividad.
- **Plasma KDE**: Alta personalización, efectos gráficos avanzados y un consumo moderado de recursos.
- **Xfce**: Ligero y rápido, ideal para equipos con pocos recursos. Usa menos memoria RAM y CPU en comparación con GNOME y KDE.

---

### 5. Intérprete de Comandos

#### 5.1. Diferencia entre Usuario Normal y Superusuario
El **superusuario (root)** tiene permisos completos en el sistema, mientras que un usuario normal solo puede modificar sus propios archivos. Para ejecutar comandos administrativos, se usa `sudo`.

#### 5.2. Uso del Comando `ls`
- `ls -l`: Lista archivos con detalles.
- `ls -a`: Muestra archivos ocultos.
- `ls -lh`: Muestra tamaños de archivos en formato legible.

#### 5.3. Cambio de Contraseña de Root
Ejecutar: `sudo passwd root`

---

### 6. Estructura de Directorios

#### 6.1. Directorios Importantes
| Descripción | Directorio |
|-------------|-------------|
| Archivos de configuración | `/etc/` |
| Directorio personal | `/home/usuario/` |
| Binarios esenciales | `/bin/` y `/usr/bin/` |
| Archivos temporales | `/tmp/` |

#### 6.2. Sistema de Archivos Raíz
El **root (`/`)** es el directorio base del sistema. Todos los demás directorios cuelgan de él y contienen datos esenciales para el funcionamiento del sistema operativo.

---

### 7. Gestión de Software (MUY DETALLADO)

#### 7.1. Gestores de Paquetes
Un **gestor de paquetes** facilita la instalación, actualización y eliminación de software en Linux. Se encarga de resolver dependencias y administrar versiones de programas. Los principales gestores según la distribución son:

- **APT (Advanced Package Tool)**: Utilizado en Debian y Ubuntu para manejar paquetes `.deb`.
- **YUM/DNF**: Usado en Fedora y Red Hat, maneja paquetes `.rpm` y optimiza dependencias.
- **Pacman**: Propio de Arch Linux, maneja `.pkg.tar.xz`, rápido y minimalista.
- **Zypper**: Gestor de paquetes de openSUSE que usa `.rpm` con administración avanzada de repositorios.

#### 7.2. Uso del Gestor de Paquetes APT

- **Buscar un paquete**:
  ```bash
  apt search nombre_del_paquete
  ```
- **Mostrar detalles de un paquete**:
  ```bash
  apt show nombre_del_paquete
  ```
- **Instalar un paquete**:
  ```bash
  sudo apt install nombre_del_paquete
  ```
- **Eliminar un paquete y sus archivos de configuración**:
  ```bash
  sudo apt remove --purge nombre_del_paquete
  ```
- **Actualizar la lista de paquetes**:
  ```bash
  sudo apt update
  ```
- **Actualizar todos los paquetes instalados**:
  ```bash
  sudo apt upgrade
  ```
- **Eliminar paquetes innecesarios**:
  ```bash
  sudo apt autoremove
  ```

#### 7.3. Paquetes Snap
Los paquetes Snap incluyen todas sus dependencias y funcionan de forma aislada, evitando conflictos con otros paquetes del sistema. Para instalar Snap:
```bash
sudo apt install snapd
```
Para instalar aplicaciones Snap:
```bash
sudo snap install nombre_del_paquete
```
Snap permite actualizaciones automáticas y compatibilidad en diversas distribuciones.

---

### 8. Personalización del Escritorio (MUY DETALLADO)

#### 8.1. Cambio de Fondo de Pantalla
1. Ir a **Configuración > Fondo de pantalla**.
2. Seleccionar una imagen o cargar una propia.
3. Confirmar el cambio.
4. Alternativamente, usar `gsettings`:
   ```bash
   gsettings set org.gnome.desktop.background picture-uri file:///ruta/a/la/imagen
   ```

#### 8.2. Configuración de Resolución de Pantalla
1. Ir a **Configuración > Pantalla**.
2. Seleccionar la resolución deseada.
3. Aplicar cambios y confirmar.
4. Usar `xrandr`:
   ```bash
   xrandr --output HDMI-1 --mode 1920x1080
   ```

#### 8.3. Activar Esquinas Activas en GNOME
1. Instalar GNOME Tweaks:
   ```bash
   sudo apt install gnome-tweaks
   ```
2. Abrir GNOME Tweaks y activar las esquinas activas.

#### 8.4. Uso de Gnome Tweaks
GNOME Tweaks permite personalizar iconos, temas y ajustes de ventanas.

---

### 9. Administración de Usuarios (MUY DETALLADO)

#### 9.1. Creación de Usuario con Webmin
1. Acceder a Webmin en `https://localhost:10000`.
2. Ir a **Usuarios y Grupos**.
3. Hacer clic en **Agregar Usuario**.
4. Definir nombre, contraseña y grupo.
5. Configurar permisos y guardar.

#### 9.2. Creación de un Usuario desde Terminal
```bash
sudo adduser nombre_usuario
```
Para asignarlo a un grupo:
```bash
sudo usermod -aG grupo nombre_usuario
```
Para listar usuarios:
```bash
cut -d: -f1 /etc/passwd
```

#### 9.3. Diferencia entre Usuario Normal y Superusuario
- **Usuario normal**: Acceso limitado a archivos y configuraciones.
- **Superusuario (root)**: Control total del sistema, acceso con:
  ```bash
  sudo -i
  ```
  o usando `sudo` en comandos específicos:
  ```bash
  sudo comando
  ```

#### 9.4. Gestión de Permisos y Propietarios
Cada archivo y directorio en Linux tiene un conjunto de permisos que determinan quién puede leer, escribir o ejecutar el archivo. Estos permisos se asignan a tres niveles:
- **Usuario propietario** (owner): Es el usuario que creó el archivo o directorio y tiene control total sobre él.
- **Grupo**: Un conjunto de usuarios que pueden compartir permisos específicos en el archivo o directorio.
- **Otros usuarios** (others): Cualquier otro usuario del sistema que no sea ni el propietario ni pertenezca al grupo del archivo.

### Cambiar permisos con letras (modo simbólico)
En Linux, los permisos se expresan en tres letras: `r` (lectura), `w` (escritura) y `x` (ejecución). Se pueden modificar con el comando `chmod` usando la siguiente sintaxis:
```bash
chmod [quién][acción][permisos] archivo
```
- `u` (usuario propietario), `g` (grupo), `o` (otros), `a` (todos).
- `+` (agregar permiso), `-` (quitar permiso), `=` (establecer permisos específicos).

Ejemplos:
- Conceder permiso de ejecución al propietario:
  ```bash
  chmod u+x archivo
  ```
- Quitar permiso de escritura a otros usuarios:
  ```bash
  chmod o-w archivo
  ```
- Conceder permisos de lectura y ejecución a todos:
  ```bash
  chmod a+rx archivo
  ```

### Cambiar permisos con números (modo octal)
Cada permiso tiene un valor numérico:
- `r` = 4 (lectura)
- `w` = 2 (escritura)
- `x` = 1 (ejecución)

Se suman estos valores para definir permisos:
- `7` (rwx) - lectura, escritura y ejecución
- `6` (rw-) - lectura y escritura
- `5` (r-x) - lectura y ejecución
- `4` (r--) - solo lectura

Ejemplos:
- Asignar permisos `rwx` al propietario, `r-x` al grupo y `r--` a otros:
  ```bash
  chmod 755 archivo
  ```
- Permitir solo lectura y escritura al propietario y nada para los demás:
  ```bash
  chmod 600 archivo
  ```

### Cambio de propietario y grupo
Para modificar el propietario o grupo de un archivo, se usan los siguientes comandos:
- Cambiar el propietario:
  ```bash
  chown nuevo_usuario archivo
  ```
- Cambiar grupo:
  ```bash
  chgrp nuevo_grupo archivo
  ```
- Cambiar propietario y grupo al mismo tiempo:
  ```bash
  chown nuevo_usuario:nuevo_grupo archivo
  ```

### Verificación de permisos
Para verificar los permisos de un archivo o directorio, se usa:
```bash
ls -l archivo
```
Esto mostrará una línea similar a:
```bash
-rwxr-xr-- 1 usuario grupo 4096 mar 16 12:00 archivo
```
Donde:
- `rwx` → Permisos del propietario.
- `r-x` → Permisos del grupo.
- `r--` → Permisos para otros usuarios.
```bash
chmod 755 archivo
```
Para cambiar propietario:
```bash
chown usuario:grupo archivo
```
Para verificar permisos:
```bash
ls -l archivo
```

---

