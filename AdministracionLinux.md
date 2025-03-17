# **Administración básica de Linux**

# **1. Administración de Usuarios y Grupos**

## **1.1 Introducción**
Linux es un sistema operativo multiusuario que permite a múltiples usuarios acceder al mismo sistema, cada uno con sus propios permisos y configuraciones. Para garantizar la seguridad y administración adecuada, los usuarios se organizan en grupos y tienen permisos específicos sobre archivos y procesos del sistema.

Un usuario es una identidad en el sistema, con su propio directorio personal, permisos y configuración. Los grupos permiten organizar usuarios y asignarles permisos compartidos de manera eficiente. 

## **1.2 Creación de Usuarios y Grupos**

### **Usuarios**
Se pueden crear usuarios desde la terminal utilizando los siguientes comandos:

- `adduser nombre_usuario`: Crea un usuario con su directorio personal en `/home/nombre_usuario`, asigna un grupo del mismo nombre y solicita la configuración de una contraseña. 
- `passwd nombre_usuario`: Cambia la contraseña del usuario. Solo el usuario puede cambiar su propia contraseña, mientras que un administrador puede cambiar la contraseña de cualquier usuario.

Cada usuario tiene un identificador único llamado **UID (User ID)**, y su directorio personal se encuentra en `/home/nombre_usuario`.

### **Grupos**
Los grupos permiten asignar permisos de manera colectiva a varios usuarios. Los grupos pueden crearse y gestionarse con los siguientes comandos:

- `addgroup nombre_grupo`: Crea un nuevo grupo.
- `adduser nombre_usuario --ingroup nombre_grupo`: Crea un usuario y lo asigna a un grupo existente.
- `usermod -aG nombre_grupo nombre_usuario`: Añade un usuario a un grupo sin cambiar su grupo principal.

Los grupos son fundamentales para establecer permisos sobre archivos y procesos en entornos colaborativos.

### **Archivos de Configuración Importantes**
El sistema almacena información sobre los usuarios y grupos en archivos especiales:
- `/etc/passwd`: Contiene información sobre los usuarios del sistema, incluyendo su UID y directorio personal.
- `/etc/shadow`: Almacena contraseñas encriptadas de los usuarios.
- `/etc/group`: Contiene información sobre los grupos y sus miembros.

## **1.3 Modificación y Eliminación de Usuarios y Grupos**
- `usermod -d /nuevo/home nombre_usuario`: Cambia el directorio personal de un usuario.
- `usermod -g nombre_grupo nombre_usuario`: Modifica el grupo principal de un usuario.
- `userdel -r nombre_usuario`: Elimina un usuario y su directorio personal.
- `groupdel nombre_grupo`: Elimina un grupo, siempre que no tenga usuarios asociados.

---

# **2. Gestión de Archivos y Directorios**

## **2.1 Navegación y Manipulación de Archivos**

### **Comandos de Navegación**
Para moverse dentro del sistema de archivos:
- `ls -al`: Lista archivos y directorios, incluyendo los ocultos.
- `cd ruta`: Cambia de directorio.
- `pwd`: Muestra la ruta del directorio actual.
- `cd ~`: Cambia al directorio HOME del usuario.
- `cd -`: Vuelve al directorio anterior.

### **Comandos de Manipulación de Archivos**
Para crear, mover, copiar y eliminar archivos:
- `mkdir -p ruta`: Crea directorios de forma recursiva.
- `cp -r origen destino`: Copia archivos y directorios.
- `mv origen destino`: Mueve o renombra archivos.
- `rm -rf ruta`: Elimina archivos o directorios sin confirmación.
- `touch archivo`: Crea un archivo vacío.
- `echo "texto" > archivo`: Crea un archivo con contenido.
- `cat archivo`: Muestra el contenido de un archivo.
- `tr '[:lower:]' '[:upper:]' < archivo > salida.txt`: Convierte el texto a mayúsculas.
- `tr '[:upper:]' '[:lower:]' < archivo > salida.txt`: Convierte el texto a minúsculas.
- `wget -O archivo URL`: Descarga un archivo desde una URL.

---

# **3. Gestión de Dispositivos y Almacenamiento**

## **3.1 Montaje y Particionado**
Linux organiza los dispositivos de almacenamiento en el directorio `/dev/`. Cada dispositivo tiene una nomenclatura específica (ejemplo: `/dev/sda`).

### **Comandos de Particionado y Formateo**
- `fdisk -l`: Lista las particiones del sistema.
- `mkfs -t ext4 /dev/sdX`: Formatea una partición con el sistema de archivos ext4.

### **Comandos de Montaje y Desmontaje**
- `mount /dev/sdX /mnt/directorio`: Monta una partición en un directorio.
- `umount /mnt/directorio`: Desmonta una partición.
- `df -h`: Muestra el uso del espacio en disco.
- `du -sh directorio`: Indica el espacio ocupado por un directorio.

---

# **4. Permisos y Propietarios**

Los permisos y propietarios en Linux son fundamentales para garantizar la seguridad y el control del acceso a los archivos y directorios dentro del sistema. Cada archivo y directorio en Linux tiene un propietario y pertenece a un grupo. Además, se les asignan permisos específicos para definir quién puede leer, escribir o ejecutar el archivo.

## **4.1 Tipos de Permisos en Linux**
Cada archivo y directorio en Linux tiene tres tipos de permisos que se aplican a tres categorías de usuarios:

### **Categorías de Usuarios:**
1. **Usuario (u - user):** El propietario del archivo.
2. **Grupo (g - group):** Usuarios que pertenecen al mismo grupo que el propietario del archivo.
3. **Otros (o - others):** Cualquier otro usuario en el sistema que no sea ni el propietario ni un miembro del grupo.

### **Tipos de Permisos:**
1. **Lectura (r - read):** Permite ver el contenido del archivo o listar el contenido del directorio.
2. **Escritura (w - write):** Permite modificar el contenido de un archivo o agregar y eliminar archivos dentro de un directorio.
3. **Ejecución (x - execute):** Permite ejecutar un archivo si es un script o programa, o acceder a un directorio.

Los permisos se representan en un formato de 10 caracteres cuando se usa el comando `ls -l`. Un ejemplo es:
```
-rwxr--r--  1 usuario grupo 1234 Mar 21 12:34 archivo.txt
```
Los primeros 10 caracteres representan:
1. `-` → Indica que es un archivo (si fuera `d`, sería un directorio).
2. `rwx` → Permisos para el propietario.
3. `r--` → Permisos para el grupo.
4. `r--` → Permisos para otros usuarios.

## **4.2 Modificación de Permisos**

### **Usando el comando `chmod`**
El comando `chmod` se usa para cambiar los permisos de un archivo o directorio. Se puede hacer de dos maneras:

#### **1. Notación Simbólica:**
- `chmod u+x archivo`: Otorga permiso de ejecución al propietario.
- `chmod g-w archivo`: Revoca el permiso de escritura al grupo.
- `chmod o+r archivo`: Otorga permiso de lectura a otros usuarios.
- `chmod ugo+rwx archivo`: Otorga todos los permisos a todos los usuarios.

#### **2. Notación Octal:**
Cada tipo de permiso se representa con un número:
- **Lectura (r) = 4**
- **Escritura (w) = 2**
- **Ejecución (x) = 1**

Para establecer permisos, se suma el valor correspondiente para cada categoría:
- `chmod 755 archivo`: Permisos `rwxr-xr-x` (dueño tiene todos los permisos, grupo y otros solo lectura y ejecución).
- `chmod 644 archivo`: Permisos `rw-r--r--` (dueño puede leer y escribir, grupo y otros solo pueden leer).

## **4.3 Modificación de Propietario y Grupo**

### **Usando `chown` para cambiar el propietario**
El comando `chown` se usa para cambiar el propietario de un archivo o directorio.
- `chown usuario archivo`: Cambia el propietario del archivo.
- `chown usuario:grupo archivo`: Cambia el propietario y el grupo al que pertenece el archivo.
- `chown -R usuario:grupo directorio/`: Aplica el cambio de propietario y grupo a todos los archivos dentro de un directorio.

### **Usando `chgrp` para cambiar el grupo**
El comando `chgrp` se usa para cambiar solo el grupo de un archivo o directorio.
- `chgrp grupo archivo`: Cambia el grupo de un archivo.
- `chgrp -R grupo directorio/`: Cambia el grupo de todos los archivos dentro de un directorio.

## **4.4 Permisos Especiales**
### **SUID (Set User ID)**
- Permite que un programa se ejecute con los permisos del propietario en lugar del usuario que lo ejecuta.
- Se activa con `chmod u+s archivo`.
- Se representa con una `s` en los permisos: `-rwsr-xr-x`.

### **SGID (Set Group ID)**
- Los archivos creados en un directorio con SGID heredan el grupo del directorio en lugar del grupo del usuario creador.
- Se activa con `chmod g+s directorio`.
- Se representa con una `s` en la columna del grupo: `drwxr-sr-x`.

### **Sticky Bit**
- Impide que los usuarios eliminen archivos de un directorio si no son los propietarios.
- Se activa con `chmod +t directorio`.
- Se representa con una `t` al final de los permisos: `drwxrwxrwt`.

---

# **5. Procesos y Gestión del Sistema**

## **5.1 Comandos de Gestión de Procesos**

Los procesos en Linux son instancias de programas en ejecución. Cada proceso tiene un identificador único llamado **PID (Process ID)** y puede estar en diferentes estados, como:

- **Ejecutándose:** El proceso está activo y utilizando recursos del sistema.
- **En espera:** Está pausado hasta recibir un evento (como la finalización de otro proceso).
- **Detenido:** Se ha pausado manualmente mediante señales del sistema.

### **Comandos para visualizar procesos**
- `ps -ef`: Muestra todos los procesos en ejecución con detalles como usuario, PID y el comando que los inició.
- `top`: Muestra los procesos en tiempo real, ordenados por uso de CPU o memoria.
- `htop`: Alternativa más avanzada a `top`, que permite una administración interactiva de procesos.

### **Finalización de procesos**
- `kill PID`: Envía una señal para finalizar un proceso de manera controlada.
- `kill -9 PID`: Termina un proceso forzadamente con la señal SIGKILL.
- `pkill nombre_proceso`: Mata todos los procesos con el nombre especificado.
- `killall nombre_proceso`: Similar a `pkill`, pero más exacto.

### **Administración de procesos en segundo plano**
- `jobs`: Muestra los trabajos en segundo plano en la terminal actual.
- `fg %n`: Trae un proceso en segundo plano de vuelta a primer plano.
- `bg %n`: Reanuda un proceso en segundo plano.

### **Prioridades de procesos**
- `nice -n 10 comando`: Ejecuta un proceso con prioridad específica (de -20 a 19, donde -20 es la prioridad más alta).
- `renice -5 -p PID`: Cambia la prioridad de un proceso en ejecución.

### **Comandos de apagado y reinicio**
- `shutdown -h +5`: Programa el apagado en 5 minutos.
- `shutdown -c`: Cancela un apagado programado.
- `reboot`: Reinicia el sistema.

---

# **6. Información del Sistema y Registros**

El monitoreo del sistema permite diagnosticar problemas y optimizar el rendimiento.

## **6.1 Comandos Informativos**

### **Información del kernel y arquitectura**
- `uname -r`: Muestra la versión del kernel.
- `uname -a`: Muestra información detallada del kernel y el sistema operativo.
- `hostnamectl`: Muestra detalles del sistema, incluyendo su arquitectura.

### **Información del procesador**
- `lscpu`: Muestra detalles como cantidad de núcleos, arquitectura y velocidad del procesador.
- `cat /proc/cpuinfo`: Muestra información detallada del procesador.

### **Memoria RAM y uso del swap**
- `free -h`: Muestra el uso de la memoria RAM y de intercambio en formato legible.
- `vmstat 1 5`: Muestra estadísticas de la memoria y del uso de CPU en intervalos de 1 segundo durante 5 veces.

### **Espacio en disco y almacenamiento**
- `df -h`: Indica el uso del espacio en disco por partición en formato legible.
- `du -sh directorio`: Muestra el tamaño total de un directorio.
- `lsblk`: Muestra información sobre los dispositivos de almacenamiento y sus particiones.

### **Registros del sistema**
- `tail -n 20 /var/log/syslog`: Muestra las últimas 20 líneas del registro del sistema.
- `dmesg | tail -20`: Muestra los últimos mensajes del kernel.

---

# **7. Tareas Programadas**

## **7.1 Automatización con cron**

El demonio `cron` permite programar la ejecución de tareas en intervalos definidos.

### **Comandos para gestionar cron**
- `crontab -e`: Abre el editor para programar tareas automáticas.
- `crontab -l`: Lista las tareas programadas del usuario actual.
- `crontab -r`: Elimina todas las tareas programadas del usuario.

### **Sintaxis de cron**
Cada línea en crontab sigue el siguiente formato:
```
* * * * * comando_a_ejecutar
│ │ │ │ │
│ │ │ │ └── Día de la semana (0-7, donde 0 y 7 son domingo)
│ │ │ └──── Mes (1-12)
│ │ └────── Día del mes (1-31)
│ └──────── Hora (0-23)
└────────── Minuto (0-59)
```

### **Ejemplo de cron**
Ejecutar un script todos los días a las 2:30 AM:
```
30 2 * * * /ruta/del/script.sh
```

---

# **8. Scripting en Linux**

Los scripts en Linux permiten automatizar tareas mediante archivos ejecutables que contienen comandos del sistema. Se escriben en Shell Script y generalmente tienen la extensión `.sh`.

## **8.1 Estructura de un Script Básico**
```bash
#!/bin/bash
echo "Hola, este es un script en Bash"
mkdir ~/nueva_carpeta
ls -l ~/nueva_carpeta
```

## **8.2 Permisos de Ejecución**
Para ejecutar un script, primero se le deben otorgar permisos de ejecución:
```bash
chmod +x script.sh
./script.sh
```

## **8.3 Variables en Bash**
```bash
mensaje="Hola Mundo"
echo $mensaje
```

## **8.4 Condicionales**
```bash
if [ -f archivo.txt ]; then
    echo "El archivo existe."
else
    echo "El archivo no existe."
fi
```

## **8.5 Bucles**
```bash
for i in {1..5}; do
    echo "Iteración $i"
done
```

## **8.6 Parámetros en Scripts**
Los scripts pueden aceptar parámetros desde la línea de comandos:
```bash
#!/bin/bash
echo "El primer parámetro es: $1"
echo "El segundo parámetro es: $2"
```
Ejemplo de ejecución:
```bash
./script.sh Hola Mundo
```
Salida:
```
El primer parámetro es: Hola
El segundo parámetro es: Mundo
```

## **8.7 Redirección y Manejo de Errores**
- `comando > salida.txt`: Guarda la salida en un archivo.
- `comando >> salida.txt`: Añade la salida al archivo sin sobrescribirlo.
- `comando 2> error.txt`: Guarda los errores en un archivo.
- `comando &> salida.txt`: Guarda salida y errores en el mismo archivo.

---


