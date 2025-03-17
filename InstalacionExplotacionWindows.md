**INSTALACIÓN Y EXPLOTACIÓN DE WINDOWS**

## 1. Introducción

Windows es uno de los sistemas operativos más utilizados en el mundo, especialmente en entornos de oficina y hogar. Su versatilidad y facilidad de uso lo convierten en una opción popular para usuarios de distintos niveles técnicos. Este documento detalla el proceso de instalación de Windows 10 en una máquina virtual, la configuración del sistema, la gestión de particiones, el uso de la terminal de comandos y la configuración del arranque dual. Además, se incluyen explicaciones detalladas sobre las versiones de Windows, su ciclo de vida y comandos esenciales del sistema operativo.

---

## 2. Instalación de Windows 10 en VirtualBox

### 2.1. Creación de una máquina virtual

Para practicar la instalación de Windows 10, se debe configurar una máquina virtual en **VirtualBox** con las siguientes características:

- Descargar la imagen **ISO** de Windows 10 (64 bits) desde el sitio web oficial de Microsoft.
- Crear una **máquina virtual** con:
  - Nombre: *Windows10Sistemas*
  - **Memoria RAM**: Al menos 2GB para un rendimiento aceptable.
  - **Disco duro virtual**: 100GB en formato VDI (Virtual Disk Image), con asignación dinámica.
  - **Procesador**: Al menos 1 núcleo, aunque se recomienda 2 o más para un mejor rendimiento.
- Configurar la máquina virtual para arrancar desde la imagen ISO descargada.
- Instalar Windows 10 en una partición de **50GB**.
- Crear un usuario con el primer apellido del alumno.

### 2.2. Instalación de Guest Additions

Las **Guest Additions** son un conjunto de herramientas que mejoran la integración entre el sistema anfitrión y la máquina virtual. Sus beneficios incluyen:

- **Mejor rendimiento gráfico**, permitiendo resoluciones más altas y aceleración 3D.
- **Habilitación del portapapeles compartido** y carpetas compartidas entre el anfitrión y la máquina virtual.
- **Integración del puntero del ratón**, eliminando la necesidad de capturarlo manualmente.
- **Sincronización del reloj del sistema**, evitando desajustes de tiempo entre el anfitrión y la VM.

Para instalar Guest Additions, una vez dentro de Windows en la máquina virtual:

1. Insertar la imagen de Guest Additions desde el menú de VirtualBox.
2. Ejecutar el instalador y seguir las instrucciones.
3. Reiniciar la máquina virtual para aplicar los cambios.

---

## 3. Explotación de Windows y Particiones

### 3.1. Instalación de un segundo Windows 10

Para instalar un segundo Windows 10 y configurar un arranque dual, se deben seguir los siguientes pasos detalladamente:

1. **Creación de una nueva partición de 30GB:**
   - Abrir el Administrador de Discos (`diskmgmt.msc` en el menú Ejecutar `Win + R`).
   - Seleccionar el disco donde se instalará el segundo sistema.
   - Reducir el tamaño de una partición existente para crear espacio no asignado.
   - Crear una nueva partición de 30GB en el espacio no asignado.
   - Formatear la partición en **NTFS**.

2. **Preparación de la instalación:**
   - Descargar la imagen ISO de Windows 10 desde la página oficial de Microsoft.
   - Montar la ISO en la máquina virtual o grabarla en un USB con **Rufus** si se trata de un equipo físico.

3. **Instalación de Windows 10 en la nueva partición:**
   - Arrancar desde el medio de instalación.
   - Seleccionar **Instalación Personalizada (Avanzada)**.
   - Elegir la nueva partición creada para instalar el sistema.
   - Completar la instalación siguiendo las indicaciones.

4. **Verificación del gestor de arranque:**
   - Reiniciar el sistema.
   - En la pantalla de selección de sistema operativo, verificar que aparecen ambas instalaciones de Windows 10.

5. **Modificar el gestor de arranque con `bcdedit`** para renombrar las opciones correctamente:
   ```cmd
   bcdedit /set {current} description "Windows 10 Turno mañana"
   bcdedit /set {default} description "Windows 10 Turno tarde"
   ```
   - `{current}` hace referencia al sistema operativo en uso.
   - `{default}` apunta al sistema predeterminado de arranque.

6. **Capturar la pantalla del gestor de arranque** tras realizar los cambios para verificar que los nombres han sido aplicados correctamente.

### 3.2. Uso de comandos en CMD

El Símbolo del Sistema (**CMD**) permite realizar múltiples tareas de administración y configuración del sistema. A continuación, se explican comandos fundamentales para la administración de archivos y configuración de discos.

#### **Comandos básicos**
- **Cambio de fecha del sistema:**
  ```cmd
  DATE 20-12-18
  ```
  Este comando cambia la fecha del sistema al 20 de diciembre de 2018.

- **Cambio de etiqueta de partición:**
  ```cmd
  LABEL C: WIN_APELLIDO
  ```
  Permite cambiar la etiqueta del volumen **C:** a `WIN_APELLIDO`.

- **Listar archivos en C:\Windows que empiecen con "w":**
  ```cmd
  DIR C:\Windows\w* /S
  ```
  Lista todos los archivos en el directorio **C:\Windows** que comiencen con la letra `w`, incluyendo subdirectorios.

#### **Administración de archivos y directorios**
- **Creación de una estructura de carpetas y archivos:**
  ```cmd
  MKDIR C:\SISTEMAS\DOS\MANUAL
  ECHO "Contenido del manual" > C:\SISTEMAS\DOS\MANUAL\manual.txt
  ```
  Esto crea un directorio anidado y un archivo de texto dentro.

- **Copiar todos los archivos de un directorio a otro:**
  ```cmd
  COPY C:\SISTEMAS\EJERCICIOS\*.* C:\
  ```
  Copia todos los archivos de la carpeta **EJERCICIOS** a la raíz del disco.

- **Buscar un archivo específico en todo el disco:**
  ```cmd
  DIR C:\ /S | FIND "nombre_archivo"
  ```
  Muestra todas las ubicaciones en el disco donde se encuentra `nombre_archivo`.

---

## 4. Versiones de Windows y Ciclo de Vida

Microsoft ha lanzado diferentes versiones de Windows, cada una con características específicas orientadas a distintos tipos de usuarios.

### **4.1. Principales versiones de Windows 10**
| Versión                   | Uso principal            | Características clave                             |
|---------------------------|------------------------|-------------------------------------------------|
| **Windows 10 Home**       | Uso doméstico          | Licencia OEM, sin soporte de dominio.           |
| **Windows 10 Pro**        | Empresas y profesionales | Conexión a dominio, BitLocker, escritorio remoto. |
| **Windows 10 Enterprise** | Empresas grandes       | Licencias por volumen, características avanzadas. |

### **4.2. Ciclo de vida de Windows**

- **Directiva Moderna:** Windows 10 recibe actualizaciones cada 6 meses.
- **Directiva Fija:** Windows 7 y 8 tenían 5 años de soporte estándar + 5 años de soporte extendido.
- **Soporte extendido:** Windows 7 dejó de recibir soporte en 2020; Windows 8.1 en 2023.

---

## 5. Particiones de Disco y Sistemas de Archivos

### **5.1. Tipos de particiones**

En un disco duro, la información se organiza en particiones, que son divisiones lógicas del almacenamiento. Existen dos tipos principales de particiones: **MBR** y **GPT**.

- **MBR (Master Boot Record):**
  - Soporta hasta 4 particiones primarias.
  - Puede contener una partición extendida con múltiples particiones lógicas.
  - No es compatible con discos mayores de 2TB.
  - Utiliza una tabla de particiones ubicada en el primer sector del disco.
  - Solo admite BIOS para el arranque del sistema.

- **GPT (GUID Partition Table):**
  - Admite hasta 128 particiones primarias.
  - Compatible con discos superiores a 2TB.
  - Requiere UEFI en lugar de BIOS.
  - Ofrece una mayor fiabilidad y seguridad, ya que almacena múltiples copias de la tabla de particiones.
  - Soporta discos dinámicos, lo que permite configuraciones avanzadas como RAID.

**Diferencias entre MBR y GPT:**
| Característica | MBR | GPT |
|--------------|-----|-----|
| Número máximo de particiones | 4 primarias o 3 primarias + 1 extendida | 128 primarias |
| Capacidad máxima del disco | 2TB | 9.4ZB (teórico) |
| Compatibilidad | BIOS | UEFI |
| Seguridad | Almacena la tabla de particiones en un solo sector | Almacena múltiples copias de la tabla de particiones |
| Fiabilidad | Mayor riesgo de corrupción | Mayor resistencia a errores |

#### **5.1.1. Tipos de particiones dentro de un disco**

Las particiones dentro de un disco pueden clasificarse en:
- **Primaria:** Contiene un sistema operativo y es arrancable.
- **Extendida:** Permite crear particiones lógicas dentro de ella.
- **Lógica:** Se encuentran dentro de una partición extendida y pueden almacenar datos.

### **5.2. Sistemas de archivos**

Cada partición debe tener un **sistema de archivos**, que define cómo se organizan los datos en el disco.

| Sistema | Uso principal           | Características y limitaciones |
|---------|-------------------------|----------------------------------|
| **FAT16** | Dispositivos antiguos   | Soporta discos de hasta 2GB. Límite de archivos por directorio de 512. |
| **FAT32** | Pendrives, discos USB   | No admite archivos mayores a 4GB. Compatible con la mayoría de los sistemas operativos. |
| **NTFS** | Discos duros modernos   | Seguridad mejorada, permisos de usuario, soporte para archivos mayores a 4GB. |
| **exFAT** | Almacenamiento externo  | Compatible con archivos grandes, diseñado para unidades flash y SD. |
| **ext4** | Linux                   | Sistema de archivos usado en la mayoría de distribuciones Linux, mayor rendimiento. |
| **HFS+** | macOS                   | Sistema de archivos para equipos Apple antes de APFS. |

#### **5.2.1. Características avanzadas de los sistemas de archivos**

- **FAT32** es el más compatible, pero no permite archivos de más de 4GB.
- **NTFS** es el más avanzado para Windows, con soporte de permisos, cifrado y tolerancia a fallos.
- **exFAT** es ideal para unidades externas, ya que no tiene las restricciones de FAT32.
- **ext4** es el estándar en Linux por su estabilidad y rendimiento.
- **HFS+** y **APFS** están optimizados para sistemas Apple y tienen soporte para instantáneas y cifrado avanzado.

### **5.3. Herramientas de administración de discos y particiones**

Para gestionar particiones y sistemas de archivos en Windows, se pueden utilizar varias herramientas:
- **Administrador de discos (`diskmgmt.msc`)**: Permite crear, eliminar y formatear particiones.
- **Diskpart**: Herramienta de línea de comandos avanzada para gestionar discos y particiones.
- **GParted**: Software libre para Linux que permite modificar particiones sin pérdida de datos.
- **EaseUS Partition Master**: Herramienta de terceros para administrar particiones de manera más flexible.

#### **5.3.1. Creación y formateo de una partición en Windows**

1. Abrir el Administrador de discos (`diskmgmt.msc`).
2. Hacer clic derecho sobre el espacio no asignado y seleccionar "Nuevo volumen simple".
3. Elegir el tamaño de la partición y asignarle una letra.
4. Seleccionar un sistema de archivos (NTFS recomendado para Windows).
5. Hacer clic en "Formatear" y luego en "Finalizar".

---

## 6. Configuración del Arranque Dual

Windows permite instalar **dos sistemas operativos** en distintas particiones y elegir cuál arrancar.

1. **Realizar la instalación del segundo Windows** como se explicó en la sección 3.1.
2. **Comprobar el gestor de arranque:**
   - Abrir CMD como administrador.
   - Ejecutar `bcdedit` para ver la configuración actual del arranque.
   - Si es necesario, modificarlo con:
     ```cmd
     bcdedit /set {current} description "Windows 10 Alternativo"
     ```
3. **Usar herramientas adicionales:** Se puede utilizar **EasyBCD** para una gestión más visual del arranque.
---

## 7. Terminal de Comandos de Windows

La terminal de comandos de Windows, conocida como **Símbolo del Sistema (CMD)**, permite a los usuarios ejecutar instrucciones de texto para interactuar con el sistema operativo. Esto es útil para automatizar tareas, administrar archivos y realizar operaciones avanzadas que no siempre son accesibles desde la interfaz gráfica.

### 7.1. Comandos básicos
Algunos comandos fundamentales incluyen:

- `CLS`: Limpia la pantalla de la terminal.
- `DIR`: Muestra el contenido de un directorio.
- `CD`: Cambia de directorio.
- `MKDIR` o `MD`: Crea un nuevo directorio.
- `RMDIR` o `RD`: Elimina un directorio vacío.
- `DEL`: Borra archivos específicos.
- `COPY`: Copia archivos de un lugar a otro.
- `MOVE`: Mueve archivos a una nueva ubicación.
- `REN`: Renombra archivos o carpetas.
- `ATTRIB`: Modifica atributos de archivos (oculto, de solo lectura, de sistema).
- `XCOPY`: Copia archivos y directorios de manera más avanzada que `COPY`.
- `FIND`: Busca texto dentro de archivos.
- `SORT`: Ordena líneas de texto en un archivo.
- `MORE`: Muestra archivos de texto página por página.

### 7.2. Redirección de salida y tuberías
La terminal de Windows permite redirigir la salida de un comando a un archivo o usar su salida como entrada para otro comando:

- `>`: Redirige la salida de un comando a un archivo (sobreescribe el contenido).
  ```cmd
  DIR C:\ > lista_archivos.txt
  ```
- `>>`: Añade la salida de un comando a un archivo sin sobrescribirlo.
  ```cmd
  ECHO "Nueva entrada" >> lista_archivos.txt
  ```
- `|` (Tubería): Conecta la salida de un comando con otro comando.
  ```cmd
  DIR C:\ | MORE
  ```
- `FIND`: Filtra la salida de un comando para buscar palabras clave.
  ```cmd
  DIR C:\Windows | FIND "System32"
  ```
- `SORT`: Ordena la salida de un comando.
  ```cmd
  DIR C:\Windows | SORT
  ```

---

## 8. Archivos por lotes (Batch Files)

Los archivos por lotes son secuencias de comandos de Windows almacenadas en archivos de texto con extensión `.bat`. Se utilizan para automatizar tareas mediante la ejecución de múltiples comandos de la terminal en orden secuencial.

### 8.1. Creación de un archivo por lotes
Para crear un archivo por lotes:
1. Abrir **Bloc de notas** u otro editor de texto.
2. Escribir los comandos deseados.
3. Guardar el archivo con extensión `.bat`.
4. Ejecutarlo haciendo doble clic sobre él o desde CMD.

Ejemplo de un archivo por lotes que muestra información del sistema:
```cmd
@ECHO OFF
ECHO Mostrando información del sistema...
SYSTEMINFO
PAUSE
```

### 8.2. Instrucciones clave en Batch
- `@ECHO OFF`: Evita que los comandos se muestren en la pantalla al ejecutarse.
- `ECHO`: Muestra texto en la pantalla.
- `PAUSE`: Detiene la ejecución hasta que el usuario presione una tecla.
- `GOTO`: Redirige la ejecución a otra parte del archivo.
- `IF`: Evalúa condiciones y ejecuta comandos en función del resultado.
- `FOR`: Ejecuta comandos en bucles.

Ejemplo de menú interactivo en Batch:
```cmd
@ECHO OFF
ECHO 1. Mostrar fecha y hora
ECHO 2. Listar archivos en C:\
ECHO 3. Salir
SET /P opcion=Ingrese su elección: 
IF %opcion%==1 DATE /T & TIME /T
IF %opcion%==2 DIR C:\
IF %opcion%==3 EXIT
PAUSE
```

### 8.3. Aplicaciones de los archivos por lotes
- Automatización de copias de seguridad con `XCOPY`.
- Creación de accesos rápidos a programas.
- Gestión de archivos en múltiples ubicaciones.
- Configuración de sistemas mediante secuencias de comandos.


