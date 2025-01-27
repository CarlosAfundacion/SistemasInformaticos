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

- **`tar`**: Crea o extrae archivos comprimidos en formato `.tar`.
  - **`-c`**: Crea un archivo comprimido.
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

**Ejercicios**

**Primera parte**
1. Listar todos los archivos del directorio `bin`.
2. Listar todos los archivos del directorio `tmp`.
3. Listar todos los archivos, incluidos los ocultos, del directorio raíz.
4. Listar todos los archivos del directorio `usr` y sus subdirectorios.
5. Cambiarse al directorio `tmp`.
6. Verificar que el directorio actual ha cambiado.
7. Mostrar el día y la hora actual.
8. Con un solo comando posicionarse en el directorio `HOME`.
9. Verificar que se está en él.
10. Cambiarse al directorio `Imágenes`.
11. Con un solo comando vuelve al directorio anterior sin escribir el nombre del directorio.
12. Ir al directorio raíz y con un solo comando entrar en el directorio `boot` y luego en el directorio `grub`.
13. Limpiar la consola.
14. Desde el directorio raíz, listar con un solo comando todos los archivos del directorio `conf.d`, que se encuentra dentro del directorio `mysql`, ubicado en el directorio `etc`.
15. Crear un nuevo documento en el escritorio llamado `primerDocumento` que contenga el mensaje: "Este es mi primer documento".
16. Crear un nuevo documento en el escritorio llamado `segundoDocumento`, cuyo contenido sea el contenido de `primerDocumento` pero en mayúsculas.
17. Crear otro documento en el escritorio llamado `tercerDocumento.txt` que contenga el mensaje: "este es mi TERCER DOCUMENTO".
18. Crear un cuarto fichero llamado `cuartoFichero.txt`, cuyo contenido sea el contenido del tercer fichero en minúsculas.
19. Crear desde el directorio raíz un nuevo directorio llamado `Prueba`.
20. Crear desde el directorio raíz un nuevo documento dentro del directorio `Prueba` que se llame `primerDocumento`.
21. Descargar una imagen y almacenarla en la carpeta `Descargas`.
22. Ir al directorio `Descargas` y realizar una copia de la imagen descargada al directorio `Prueba`.
23. Ir al directorio raíz.
24. Verificar que el directorio actual ha cambiado.
25. Realizar una copia desde el directorio raíz del fichero `primerDocumento` que se encuentra en el directorio `Prueba` al escritorio.
26. Mostrar la fecha y la hora.
27. Desde el directorio raíz, mover el fichero `primerDocumento` que se encuentra en el escritorio al directorio `Descargas`.
28. Cambiar el nombre de `primerDocumento` por `primerDocumentoModificado.txt`.

