## **Administración Linux**

###  **Ejercicio 1 – Usuarios y grupos**

1. Crea los siguientes usuarios en el sistema: `mario`, `lucia`, `sergio` y `nerea`.  
   - Asigna a `mario` y `lucia` el grupo principal `marketing`.  
   - Asigna a `sergio` y `nerea` el grupo principal `rrhh`.  
   - Utiliza como contraseña el mismo nombre de usuario.  
   Verifica su correcta creación consultando `/etc/passwd`, `/etc/group` y `/etc/shadow`.

---

###  **Ejercicio 2 – Dispositivos**

2. Monta una imagen ISO de cualquier distribución Linux (puede ser Ubuntu Desktop) en el sistema.  
   - Identifica y anota el dispositivo asociado (por ejemplo `/dev/sr0`) y el punto de montaje.  
   - Muestra por pantalla la lista de archivos del medio montado.

---

###  **Ejercicio 3 – Discos y particiones**

3. Crea una nueva partición lógica de aproximadamente **1 GB** en el espacio libre del disco virtual.  
   - Formatea la partición con el sistema de archivos **ext4**.  
   - Móntala en el directorio `/mnt/proyectos` y asegúrate de que puede escribirse en ella.  
   - Configura su montaje automático al iniciar el sistema editando `/etc/fstab`.

---

###  **Ejercicio 4 – Permisos**

4. Inicia sesión como el usuario `lucia` y crea un script llamado `respaldo.sh` que copie todos los archivos `.txt` del directorio actual al directorio `~/Respaldo`.  
   - Cambia los permisos del script para que solo el propietario pueda leer, escribir y ejecutar el archivo.  
   - Modifica después los permisos para que cualquier usuario del sistema pueda ejecutarlo pero no modificarlo.

---

###  **Ejercicio 5 – Procesos**

5. Crea un script llamado `loop.sh` que contenga un bucle infinito (`while true; do ... done`).  
   - Ejecútalo en segundo plano, localiza su PID y finaliza el proceso desde otra terminal.  
   - Consulta el PID del proceso padre (`PPID`) y anótalo.  
   - Ejecuta el comando `top` y observa cuánta CPU está usando el proceso antes de finalizarlo.

---

###  **Ejercicio 6 – Información del sistema**

6. Mediante los comandos adecuados, responde:  
   - ¿Qué versión del kernel tiene tu sistema?  
   - ¿Qué memoria RAM está instalada y cuánto se está usando?  
   - ¿Cuántos procesos están actualmente en ejecución?  
   - ¿Qué usuario está ocupando más memoria RAM?

---

###  **Ejercicio 7 – Tareas programadas**

7. Crea un script llamado `informe.sh` que guarde en el archivo `estado_sistema.txt` lo siguiente:
   - Fecha y hora actuales.  
   - Espacio en disco disponible.  
   - Número de procesos activos.  
   Luego, programa su ejecución diaria a las 13:00 de lunes a viernes con `crontab`.

---

## **Comandos Linux**

###  **Navegación y gestión de archivos (1–10)**

1. Lista todos los archivos (incluidos ocultos) del directorio `/home` con formato detallado.  
2. Cambia al directorio `/etc/network` y muestra la ruta absoluta actual.  
3. Vuelve al directorio anterior sin escribir su nombre.  
4. Crea un directorio llamado `PrácticasLinux` dentro del directorio `Documentos`.  
5. Crea un archivo llamado `resumen.txt` dentro del directorio `PrácticasLinux` que contenga el texto: "Resumen de comandos de Linux".  
6. Añade al final del archivo `resumen.txt` la línea: "Comando ls: lista archivos".  
7. Muestra el contenido del archivo `resumen.txt` por pantalla.  
8. Elimina el archivo `resumen.txt`.  
9. Copia todos los archivos del directorio `/etc/skel` al directorio `PrácticasLinux`.  
10. Mueve el directorio `PrácticasLinux` al escritorio.  

---

## **Adminsitración Windows**

### **Ejercicio 1 – Fecha del sistema y etiquetas**

1. Cambia la fecha del sistema al **1 de septiembre de 2020** utilizando el comando adecuado.  
   Cambia la **etiqueta de la unidad C:** a tu nombre seguido de la palabra `ALUMNO`.  
   _(Ejemplo: si te llamas Laura Pérez → `LAURA_ALUMNO`)_

---

### **Ejercicio 2 – Búsqueda avanzada de archivos**

2. Realiza una búsqueda desde `C:\Windows` para mostrar todos los archivos y carpetas **que tengan exactamente 6 letras en el nombre**, independientemente de la extensión.  
   La búsqueda debe incluir **subdirectorios**.

---

### **Ejercicio 3 – Creación de estructura de directorios y archivos**

3. Crea la siguiente estructura de carpetas y archivos en la unidad `C:`:
```
C:\
└── REDES
    ├── CONFIG
    │   └── ipconfig.txt
    └── DOCUMENTOS
        ├── red1.txt
        └── red2.txt
```
- Utiliza rutas **absolutas** para `ipconfig.txt`.  
- Usa rutas **relativas** para los demás archivos.

---

### **Ejercicio 4 – Copias y conversiones de archivos**

4. Realiza las siguientes acciones:
- Copia todos los archivos de `C:\REDES\DOCUMENTOS` al directorio raíz de `C:`.  
- Crea un directorio `RED_PRACTICA` en `C:` y copia dentro el archivo `ipconfig.txt`, renombrándolo como `IPDETALLADA.TXT`.  
- Copia todos los archivos `.txt` de `DOCUMENTOS` a `CONFIG`, cambiando su extensión a `.res`.

---

###  **Ejercicio 5 – Atributos y contenido**

5. Establece los atributos **sistema** y **oculto** al archivo `red1.res` ubicado en `C:\REDES\CONFIG`.  
   A continuación:  
   - Muestra el contenido de `ipconfig.txt` y `red2.txt`.  
   - Añade el contenido de `red2.txt` al final de `ipconfig.txt`, sin eliminar su contenido original.

---

### **Ejercicio 6 – Archivos por lotes**

6. Crea un archivo por lotes llamado `resumen.bat` que realice las siguientes tareas:  
   - Guarde en `hoy.txt` la lista de todos los archivos modificados **en la fecha actual** en `C:\Windows`.  
   - Apague el sistema con una cuenta atrás de **30 segundos**.

---

### **Ejercicio 7 – Árbol de directorios y filtros**

7. Genera un archivo llamado `estructura.txt` que contenga el árbol completo de directorios de `C:\`.  
   - A continuación, crea un archivo `solo_txt.txt` con la lista de todos los archivos `.txt` que se encuentren dentro de `C:\Users`.  
   - Finalmente, crea un archivo `ocultos.txt` con todos los archivos que tengan el atributo de oculto en el sistema.

---


