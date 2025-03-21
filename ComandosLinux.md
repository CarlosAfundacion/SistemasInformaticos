**Práctica de comandos Linux**

**Introducción**

En esta actividad, practicarás una serie de comandos esenciales de Linux para gestionar el sistema operativo, archivos, directorios, usuarios y procesos. A continuación, se describen algunos de los comandos necesarios para resolver los ejercicios:

Aquí tienes una descripción detallada de los comandos y modificadores utilizados en estas prácticas:

---

### **Comandos básicos de navegación y gestión de archivos**

- **`ls`**: Lista el contenido de un directorio.
  - **`-a`**: Muestra también los archivos ocultos (los que empiezan con `.`).
  - **`-R`**: Lista de manera recursiva todos los archivos y subdirectorios.
  - **`-l`**: Muestra detalles como permisos, tamaño y propietario.
  - **`-h`**: Convierte los tamaños de archivo a un formato legible (por ejemplo, KB, MB).

- **`cd`**: Cambia el directorio de trabajo.
  - **`-`**: Vuelve al directorio anterior.
  - **`~`**: Cambia al directorio HOME del usuario actual.

- **`pwd`**: Muestra la ruta completa del directorio actual.

- **`mkdir`**: Crea uno o varios directorios.
  - **`-p`**: Crea directorios de manera recursiva.

- **`cp`**: Copia archivos o directorios.
  - **`-r`**: Copia directorios de manera recursiva.
  - **`-u`**: Copia solo archivos más recientes que el destino.

- **`mv`**: Mueve o renombra archivos y directorios.

- **`rm`**: Elimina archivos o directorios.
  - **`-r`**: Elimina directorios de forma recursiva.
  - **`-f`**: Fuerza la eliminación sin pedir confirmación.

- **`touch`**: Crea archivos vacíos.

- **`echo`**: Muestra texto en la salida estándar o lo escribe en un archivo.
  - **`>>`**: Añade contenido al final de un archivo.

- **`cat`**: Muestra el contenido de un archivo, combina archivos o crea nuevos.
  - **`>`**: Sobrescribe el contenido del archivo.
  - **`>>`**: Añade contenido al archivo existente.

- **`tr`**: Transforma texto.
  - **`'[:lower:]' '[:upper:]'`**: Convierte el texto a mayúsculas.
  - **`'[:upper:]' '[:lower:]'`**: Convierte el texto a minúsculas.

---

### **Comandos de gestión de archivos comprimidos**

-**`-C`**: Este operador, se puede concatenar a otros comandos para posicionarse en un directorio concreto.

- **`tar`**: Crea o extrae archivos comprimidos en formato `.tar`. **En el caso de `tar`el orden de los operadores condiciona el resultado del comando**
  - **`-c`**: Crea un archivo comprimido.
  - **`-z`**: usa gzip para la compresión.
  - **`-x`**: Extrae un archivo comprimido.
  - **`-v`**: Muestra los detalles del proceso.
  - **`-f`**: Especifica el nombre del archivo comprimido.
 

- **`zip`**: Comprime archivos en formato `.zip`.
- **`unzip`**: Extrae archivos comprimidos en formato `.zip`.

- **`wget`**: Descarga archivos desde Internet.
  - **`-O`**: Especifica el nombre del archivo descargado.

---

### **Comandos de gestión del sistema**

- **`date`**: Muestra la fecha y la hora actual.

- **`cal`**: Muestra un calendario.
  - **`cal 2020`**: Muestra el calendario de todo el año 2020.
  - **`cal 07 2020`**: Muestra el calendario de julio de 2020.

- **`clear`**: Limpia la pantalla del terminal.

- **`shutdown`**: Apaga o reinicia el sistema.
  - **`now`**: Apaga el sistema de inmediato.
  - **`+2`**: Programa el apagado en 2 minutos.
  - **`-r`**: Reinicia el sistema.
  - **`-c`**: Cancela un apagado programado.

---

### **Comandos de permisos y propietarios**

- **`chmod`**: Cambia los permisos de un archivo o directorio.
  - **`u`**: Propietario del archivo.
  - **`g`**: Grupo propietario.
  - **`o`**: Otros usuarios.
  - **`+r`**: Añade permisos de lectura.
  - **`-w`**: Elimina permisos de escritura.
  - **`+x`**: Añade permisos de ejecución.

- **`chown`**: Cambia el propietario o grupo de un archivo o directorio.
  - **`<usuario>:<grupo>`**: Especifica el nuevo propietario y grupo.

---

### **Comandos para buscar archivos y contenido**

- **`find`**: Busca archivos y directorios.
  - **`-name`**: Busca por nombre.
  - **`-type d`**: Busca solo directorios.
  - **`-type f`**: Busca solo archivos.

- **`grep`**: Busca texto dentro de archivos.
  - **`-i`**: Ignora mayúsculas y minúsculas.
  - **`-c`**: Muestra cuántas veces aparece la coincidencia.
  - **`-r`**: Busca recursivamente en un directorio.

---

### **Comandos para procesos y sistema**

- **`ps`**: Muestra información sobre los procesos en ejecución.
  - **`-aux`**: Muestra todos los procesos, incluso los de otros usuarios.

- **`top`**: Muestra en tiempo real los procesos activos del sistema.

- **`kill`**: Envía señales para terminar un proceso.
  - **`-9`**: Termina de manera forzada el proceso.

---

### **Otros comandos útiles**

- **`history`**: Muestra el historial de comandos ejecutados.
- **`whoami`**: Muestra el usuario actual.
- **`head`**: Muestra las primeras líneas de un archivo.
  - **`-n <n>`**: Especifica el número de líneas a mostrar.
- **`tail`**: Muestra las últimas líneas de un archivo.
  - **`-n <n>`**: Especifica el número de líneas a mostrar.
- **`df`**: Muestra información del espacio en disco disponible.
- **`du`**: Muestra el uso del espacio en disco de archivos y directorios.

---

### **Concatenación de Comandos en Linux y Orden de los Operadores**

En Linux, puedes ejecutar múltiples comandos en una sola línea utilizando operadores de concatenación. A continuación, se explican las diferentes maneras de concatenar comandos y cómo los operadores afectan su ejecución.

---

### **1. Operadores de Concatenación de Comandos**
#### **1.1 Punto y coma (`;`)**
Este operador permite ejecutar múltiples comandos en secuencia, independientemente de si el anterior se ejecuta con éxito o no.

```bash
pwd; ls; echo "Comando ejecutado"
```
- Se ejecutarán `pwd`, `ls` y `echo` sin importar si alguno falla.

---

#### **1.2 Operador AND lógico (`&&`)**
Este operador ejecuta el segundo comando **solo si el primero se ejecuta correctamente**.

```bash
mkdir nuevo_directorio && cd nuevo_directorio
```
- Si `mkdir nuevo_directorio` tiene éxito, entonces se ejecuta `cd nuevo_directorio`.

---

#### **1.3 Operador OR lógico (`||`)**
Este operador ejecuta el segundo comando **solo si el primero falla**.

```bash
mkdir /etc/nuevo_dir || echo "No se pudo crear el directorio"
```
- Si `mkdir /etc/nuevo_dir` falla, se ejecutará `echo`.

---

#### **1.4 Operador de encadenamiento con tuberías (`|`)**
Este operador pasa la salida de un comando como entrada a otro.

```bash
ls -l | grep "documento"
```
- Lista archivos detalladamente y filtra aquellos que contienen "documento".

---

### **2. Orden de Operadores en Comandos Específicos**
Algunos comandos requieren que los operadores se coloquen en un orden específico para funcionar correctamente.

1. **`tar`**: `-czvf` (`-f` siempre antes del archivo).
2. **`chmod`**: `[quién][acción][permisos] archivo` (Ejemplo: `chmod u+rwx archivo`).
3. **`chown`**: `[usuario]:[grupo] archivo` (`chown user:group archivo`).
4. **`find`**: `[directorio] [opciones] [acción]` (`find /etc -type f -name "*.conf"`).
5. **`grep`**: `[opciones] "patrón" archivo` (`grep -i "error" syslog`).
6. **`ls`**: `[opciones] [directorio]` (`ls -lah /var/log`).
7. **`rm`**: `[opciones] archivo` (`rm -rf carpeta/`).
8. **`wget`**: `[opciones] URL` (`wget -O archivo.txt URL`).

1. **En la mayoría de los comandos, las opciones pueden ir en cualquier orden.**
2. **En comandos como `tar`, `find`, `wget`, `chmod` y `grep`, el orden de las opciones SÍ importa.**
3. **`-f` siempre va antes del archivo en `tar`, `wget` y `find`.**
4. **En `find`, `grep` y `chmod`, las opciones deben ir en una estructura lógica:**
   - **Primero filtros (`find` -type, -name).**
   - **Luego acciones (`find` -delete, `grep` -c).**
   - **En permisos (`chmod`), primero el usuario (`u`, `g`, `o`), luego la acción (`+` o `-`), y por último los permisos (`rwx`).**

### **Diferencia entre `-r` y `-R` en Comandos de Linux**  

En Linux, algunos comandos admiten tanto `-r` como `-R`, pero **su significado depende del comando en cuestión**. A continuación, explico sus diferencias según el comando en el que se usan.

---

| Comando  | `-r` | `-R` | ¿Son iguales? |
|----------|------|------|--------------|
| `rm`     | Recursivo | Recursivo | ✅ Sí |
| `cp`     | Recursivo | Recursivo | ✅ Sí |
| `ls`     | Orden inverso | Listado recursivo | ❌ No |
| `chmod`  | ❌ No existe | Recursivo | ❌ No |
| `chown`  | ❌ No existe | Recursivo | ❌ No |

 **Regla general**:
- `rm` y `cp`: `-r` y `-R` son equivalentes.
- `ls`: `-r` (inverso) y `-R` (recursivo) son diferentes.
- `chmod` y `chown`: **Solo `-R` es válido** (`-r` no existe).

**Ejercicios**

**Primera parte**
1. Listar todos los archivos del directorio `bin`.
```bash
   ls /bin
```
   
3. Listar todos los archivos del directorio `tmp`.
```bash
   ls /tmp
```
4. Listar todos los archivos, incluidos los ocultos, del directorio raíz.
```bash
   ls -a /
```
6. Listar todos los archivos del directorio `usr` y sus subdirectorios.
```bash
   ls -R /usr
```
7. Cambiarse al directorio `tmp`.
```bash
   cd /tmp
```
9. Verificar que el directorio actual ha cambiado.
```bash
  pwd
```
10. Mostrar el día y la hora actual.
```bash
   date
```
12. Con un solo comando posicionarse en el directorio `HOME`.
```bash
   cd
```
o

```bash
   cd ~
```
13. Verificar que se está en él.
```bash
   pwd
```
15. Cambiarse al directorio `Imágenes`.
```bash
   cd Imágenes
```
17. Con un solo comando vuelve al directorio anterior sin escribir el nombre del directorio.
```bash
   cd -
```

19. Ir al directorio raíz y con un solo comando entrar en el directorio `boot` y luego en el directorio `grub`.
```bash
   cd /
   cd /boot/grub
```
21. Limpiar la consola.
```bash
   clear
```
23. Desde el directorio raíz, listar con un solo comando todos los archivos del directorio `systemd`, que se encuentra dentro del directorio `lib`, ubicado en el directorio `usr`.
```bash
   ls /usr/lib/systemd
```
25. Crear un nuevo documento en el escritorio llamado `primerDocumento` que contenga el mensaje: "Este es mi primer documento".
```bash
   echo "Este es mi primer documento" > ~/Escritorio/primerDocumento
```
27. Crear un nuevo documento en el escritorio llamado `segundoDocumento`, cuyo contenido sea el contenido de `primerDocumento` pero en mayúsculas.
```bash
   cat ~/Escritorio/primerDocumento | tr '[:lower:]' '[:upper:]' > ~/Escritorio/segundoDocumento
```
29. Crear otro documento en el escritorio llamado `tercerDocumento.txt` que contenga el mensaje: "este es mi TERCER DOCUMENTO".
```bash
   echo "este es mi TERCER DOCUMENTO" > ~/Escritorio/tercerDocumento.txt
```
31. Crear un cuarto fichero llamado `cuartoFichero.txt`, cuyo contenido sea el contenido del tercer fichero en minúsculas.
```bash
   cat ~/Escritorio/tercerDocumento.txt | tr '[:upper:]' '[:lower:]' > ~/Escritorio/cuartoFichero.txt
```
33. Crear desde el directorio raíz un nuevo directorio llamado `Prueba`.
```bash
   sudo mkdir /Prueba
```
35. Crear desde el directorio raíz un nuevo documento dentro del directorio `Prueba` que se llame `primerDocumento`.
```bash
   sudo touch /Prueba/primerDocumento
```
Crea el documento sin contenido
37. Descargar una imagen y almacenarla en la carpeta `Descargas`.
```bash
   wget -O ~/Descargas/imagen.jpg https://url.com/imagenDeIntenet.jpg
```
37. Ir al directorio `Descargas` y realizar una copia de la imagen descargada al directorio `Prueba`.
```bash
   cd ~/Descargas
   cp imagen.jpg /Prueba/
``` 
39. Ir al directorio raíz.
```bash
   cd /
``` 
41. Verificar que el directorio actual ha cambiado.
```bash
   pwd
``` 
43. Realizar una copia desde el directorio raíz del fichero `primerDocumento` que se encuentra en el directorio `Prueba` al escritorio.
```bash
   cp /Prueba/primerDocumento ~/Escritorio/
``` 
45. Mostrar la fecha y la hora.
```bash
   date
``` 
47. Desde el directorio raíz, mover el fichero `primerDocumento` que se encuentra en el escritorio al directorio `Descargas`.
```bash
   mv ~/Escritorio/primerDocumento ~/Descargas/
``` 
49. Cambiar el nombre de `primerDocumento` por `primerDocumentoModificado.txt`.
```bash
   mv ~/Descargas/primerDocumento ~/Descargas/primerDocumentoModificado.txt
```
---

**Segunda parte**

#### **Comandos básicos de navegación y gestión de archivos**

**1. Listar todos los archivos y subdirectorios del directorio `var` recursivamente con formato detallado.** 
```bash
   ls -la -R /var
```
2. Crear un directorio llamado `TestRecursivo` dentro del directorio `Documentos` y, dentro de él, otro directorio llamado `SubTestRecursivo`.  
3. Copiar solo los archivos más recientes del directorio `/etc` al directorio `tmp`.  
4. Mover el directorio `SubTestRecursivo` dentro de `TestRecursivo` al directorio `Escritorio` y renombrarlo a `RenamedDir`.  
**5. Eliminar todos los archivos con extensión `.log` en el directorio `var/log` de forma recursiva y sin confirmación.**
```bash
   udo find /var/log -type f -name "*.log" -delete
```
6. Listar el contenido del directorio `/var/log` mostrando los tamaños en un formato legible.  
7. Cambiar al directorio `/etc`, luego regresar al directorio anterior sin escribir su nombre.  
8. Crear un directorio llamado `Proyecto/Linux/Ejercicios` en una sola línea.  
9. Copiar recursivamente el directorio `/etc/skel` al directorio `Documentos`.  
10. Renombrar el archivo `archivo.txt` en el directorio `Documentos` a `archivo_renombrado.txt`.  
11. Eliminar todos los archivos con extensión `.tmp` en el directorio `/tmp` sin confirmación.  
12. Añadir la línea "Este es un segundo mensaje" al archivo `mensaje.txt` en el escritorio.  
13. Sobrescribir el archivo `contenido.txt` en el escritorio con la frase "Contenido actualizado".  
14. Crear un archivo llamado `mayusculas.txt` que contenga el contenido del archivo `texto.txt` en mayúsculas.  

---

#### **Gestión de archivos comprimidos**

**15. Comprimir el directorio `Prueba` en un archivo llamado `PruebaBackup.tar.gz` utilizando compresión gzip.** 
```bash
   tar -czvf PruebaBackup.tar.gz /Prueba
```
16. Extraer el archivo comprimido `PruebaBackup.tar.gz` en un nuevo directorio llamado `PruebaRestaurada`.  
**17. Descargar un archivo `.zip` desde [internet](https://www.uv.es/fragar/html/zips/mvh_instrucciones.zip) y extraerlo en el directorio `Descargas`.**
```bash
   wget -P ~/Descargas https://www.uv.es/fragar/html/zips/mvh_instrucciones.zip
   cd ~/Descargas
   unzip mvh_instrucciones.zip
```
o
```bash
   wget -P ~/Descargas https://www.uv.es/fragar/html/zips/mvh_instrucciones.zip
   
   unzip  ~/Descargas/mvh_instrucciones.zip -d ~/Descargas/
```
El -P a diferencia del -O, mantiene el nombre del archivo tal cual se encuentra en el enlace
18. Comprimir los archivos del directorio `Documentos` en un archivo llamado `archivos.zip`.  
19. Extraer el contenido del archivo `archivos.zip` en el directorio `Extraido`.  
20. Descargar un archivo desde una [URL](https://workupload.com/start/zNtEUqDL) y guardarlo como `archivo_descargado.txt`.  

---

#### **Permisos y propietarios**

**21. Crear un directorio llamado `Seguridad` y asignarle permisos de lectura y escritura solo para el propietario.** 
```bash
   mkdir ~/Seguridad
   chmod 600 ~/Seguridad
```
22. Cambiar el propietario del archivo `/tmp/archivoPermisos.txt` a un usuario específico llamado `user1` y asignarle el grupo `users`.  
23. Cambiar los permisos de todos los archivos en el directorio `Seguridad` para que sean ejecutables por el propietario.  
24. Añadir permisos de lectura al archivo `privado.txt` para todos los usuarios.  
25. Eliminar permisos de escritura del archivo `configuracion.txt` para el propietario.  
**26. Cambiar el propietario del archivo `archivo.txt` al usuario `admin` y asignarle el grupo `root`.**
```bash
   sudo chown admin:root archivo.txt
```

---

#### **Búsqueda de archivos y contenido**

27. Buscar en el directorio `/etc` todos los archivos cuyo nombre comience con `host`.  
28. Buscar todas las líneas que contengan la palabra `root` en los archivos dentro del directorio `/etc` y contar cuántas veces aparece.  
29. Buscar todos los directorios dentro de `/var` cuyo nombre contenga la palabra `log`.  
**30. Buscar la palabra `error` en el archivo `/var/log/syslog` ignorando mayúsculas y minúsculas.**  
```bash
   grep -i "error" /var/log/syslog
```
---

#### **Gestión del sistema**

31. Mostrar el calendario completo del año 2025.  
**32. Programar un apagado del sistema para dentro de 5 minutos.**
```bash
   sudo shutdown -h +5
``` 
**33. Cancelar el apagado programado.**  
```bash
   sudo shutdown -c
```
34. Mostrar el calendario de diciembre de 2023.  

---

#### **Procesos**

35. Listar los procesos en ejecución para un usuario específico llamado `user1`.  
36. Finalizar todos los procesos que estén ejecutando un programa llamado `firefox`.  
**37. Listar todos los procesos del sistema con información detallada.**
```bash
   ps aux
``` 
**38. Finalizar el proceso con PID `1234` utilizando una señal forzada.**  
```bash
   sudo kill -9 1234
```

---

#### **Otros comandos útiles**

39. Mostrar los últimos 15 comandos ejecutados.  
40. Mostrar el usuario actual que está ejecutando los comandos.  
**41. Mostrar las primeras 5 líneas del archivo `/var/log/syslog`.**
```bash
   head -n 5 /var/log/syslog
``` 
42. Mostrar las últimas 3 líneas del archivo `/var/log/syslog`.  
**43. Mostrar el espacio en disco disponible en el sistema en formato legible.**
```bash
   df -hr
```
44. Mostrar el uso de disco del directorio `Descargas`.  

---



