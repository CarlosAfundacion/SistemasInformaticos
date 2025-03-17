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

## **4.1 Modificación de Permisos y Propietarios**
- `ls -l`: Muestra los permisos de los archivos.
- `chmod 775 archivo`: Cambia los permisos de un archivo usando notación octal.
- `chmod u+x archivo`: Otorga permiso de ejecución al propietario.
- `chown usuario:grupo archivo`: Cambia el propietario y grupo de un archivo.
- `chgrp grupo archivo`: Cambia solo el grupo propietario de un archivo.

---

# **8. Scripting en Linux**

Los scripts en Linux permiten automatizar tareas mediante archivos ejecutables que contienen comandos del sistema. Se escriben en Shell Script y generalmente tienen la extensión `.sh`.

### **Estructura de un Script Básico**
```bash
#!/bin/bash
echo "Hola, este es un script en Bash"
mkdir ~/nueva_carpeta
ls -l ~/nueva_carpeta
```

### **Permisos de Ejecución**
Para ejecutar un script, primero se le deben otorgar permisos de ejecución:
```bash
chmod +x script.sh
./script.sh
```

### **Variables en Bash**
```bash
mensaje="Hola Mundo"
echo $mensaje
```

### **Condicionales**
```bash
if [ -f archivo.txt ]; then
    echo "El archivo existe."
else
    echo "El archivo no existe."
fi
```

### **Bucles**
```bash
for i in {1..5}; do
    echo "Iteración $i"
done
```

---

# **Conclusión**
Este documento proporciona una guía detallada sobre la administración de un sistema Linux, asegurando que el usuario pueda resolver todos los ejercicios planteados.

