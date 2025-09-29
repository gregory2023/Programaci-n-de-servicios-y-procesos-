# PSP - S01 - Linux
## Actividad Resuelta con Comandos

---

## Bloque 0: Historial

### 0. Amplía el tamaño máximo del historial de la shell y configura que cada línea del historial muestre también la fecha y la hora.

```bash
nano ~/.bashrc
```

**Añadir al final del archivo:**
```bash
export HISTSIZE=10000
export HISTFILESIZE=20000
export HISTTIMEFORMAT="%F %T "
```

### 1. Comprueba que ahora, al mostrar el historial, aparece la fecha y hora junto a los comandos ejecutados.

```bash
history
```

### 2. Configura estos cambios para que sean permanentes

```bash
source ~/.bashrc
```

---

## Bloque 1: Gestión del sistema y el kernel

### 1. Muestra toda la información de tu sistema operativo y kernel.

```bash
uname -a
```

**Alternativa:**
```bash
lsb_release -a
```

### 2. Averigua únicamente la versión del kernel.

```bash
uname -r
```

### 3. Comprueba el espacio en disco disponible.

```bash
df -h
```

### 4. Calcula cuánto espacio ocupa la carpeta /etc.

```bash
du -sh /etc
```

### 5. Consulta la memoria RAM disponible y usada.

```bash
free -h
```

---

## Bloque 2: Procesos

### 6. Lanza un monitor de procesos en tiempo real y observa:

```bash
top
```

**Nota:** Para salir presiona 'q'

**Observar:**
- Número total de procesos (parte superior)
- Cuál consume más CPU (columna %CPU)
- Presionar 'q' para salir

### 7. Instala y ejecuta una versión mejorada del monitor de procesos y compárala con la anterior.

```bash
sudo apt update && sudo apt install -y htop
htop
```

### 8. Obtén un listado de todos los procesos del sistema y localiza el proceso de tu shell.

```bash
ps aux | grep bash
```

### 9. Muestra la jerarquía de procesos en forma de árbol.

```bash
pstree -p
```

### 10. Lanza el comando ping contra google.com en segundo plano (&) y obtén su identificador de proceso (PID).

```bash
ping google.com &
```

**Para ver el trabajo en segundo plano:**
```bash
jobs
```

**Para obtener el PID:**
```bash
ps aux | grep ping
```

### 11. Finaliza el proceso de Firefox usando su PID.

```bash
ps aux | grep firefox
kill -9 PID
```

**Nota:** Reemplaza PID por el número del proceso encontrado

### 12. Vuelve a lanzarlo y esta vez deténlo, luego reactívalo.

```bash
sleep 500 &
jobs
kill -STOP %1
kill -CONT %1
```

**Explicación:**
- `STOP`: Detiene el proceso
- `CONT`: Continúa el proceso detenido
- `%1`: Referencia al trabajo número 1

### 13. Crea un script que capture la señal de interrupción (Ctrl+C) y muestre un mensaje en lugar de cerrarse.

```bash
nano ctrlc.sh
```

**Contenido del script:**
```bash
#!/bin/bash
trap 'echo "Ctrl+C capturado. No me puedes cerrar así."' SIGINT
while true; do
    sleep 1
done
```

**Dar permisos de ejecución y ejecutar:**
```bash
chmod +x ctrlc.sh
./ctrlc.sh
```

---

## Bloque 3: Gestión de servicios con systemd

### 14. Consulta el estado del servicio de conexión remota (ssh).

```bash
systemctl status ssh
```

### 15. Inicia dicho servicio si está instalado.

```bash
sudo systemctl start ssh
```

### 16. Desactívalo del arranque automático y vuelve a activarlo.

```bash
sudo systemctl disable ssh
sudo systemctl enable ssh
```

---

## Bloque 4: Archivos y directorios

### 17. Lista todos los archivos, incluidos los ocultos, en tu directorio personal.

```bash
ls -a ~
```

### 18. Crea una carpeta llamada prueba.

```bash
mkdir prueba
```

### 19. Dentro de esa carpeta, crea un archivo notas.txt que contenga el texto "Hola Linux".

```bash
echo "Hola Linux" > prueba/notas.txt
```

### 20. Copia ese archivo con otro nombre.

```bash
cp prueba/notas.txt prueba/copia.txt
```

### 21. Renombra el archivo copiado.

```bash
mv prueba/copia.txt prueba/renombrado.txt
```

### 22. Borra el archivo renombrado.

```bash
rm prueba/renombrado.txt
```

---

## Bloque 5: Redirecciones y pipes

### 23. Redirige la salida de un listado de archivos a un archivo llamado listado.txt.

```bash
ls -l > listado.txt
```

### 24. Añade una nueva línea al final del mismo archivo con el texto "Fin del listado".

```bash
echo "Fin del listado" >> listado.txt
```

**Nota:** `>>` añade al final sin borrar el contenido existente

### 25. Redirige los errores (2) de una operación no válida a un dispositivo nulo para ignorarlos.

```bash
ls /dir_inexistente 2> /dev/null
```

**Explicación:**
- `2>`: Redirige stderr (errores)
- `/dev/null`: Descarta la salida

### 26. Filtra de una lista de procesos únicamente aquellos que contengan la palabra "bash".

```bash
ps aux | grep bash
```

### 27. Muestra solo las últimas 5 líneas del archivo listado.txt.

```bash
tail -n 5 listado.txt
```

---

## Bloque 6: Tuberías con nombre y sockets

### 28. Crea una tubería con nombre llamada cola.

```bash
mkfifo cola
```

### 29. Desde una terminal, deja el archivo cola en espera de datos. Desde otra terminal, escribe un mensaje en esa tubería.

**Terminal 1 (lectura - quedará esperando):**
```bash
cat < cola
```

**Terminal 2 (escritura):**
```bash
echo "Mensaje a través de la cola" > cola
```

### 30. Verifica que cola es realmente una tubería.

```bash
ls -l cola
```

**Resultado esperado:** Debe mostrar una 'p' al inicio de los permisos, indicando que es una tubería (pipe)

### 31. Establece un canal de comunicación entre dos terminales locales utilizando una herramienta que permite redirigir flujos de entrada y salida entre sockets.

**Terminal 1 (servidor en escucha):**
```bash
nc -l 12345
```

**Terminal 2 (cliente que se conecta):**
```bash
nc localhost 12345
```

**Nota:** Todo lo que escribas en una terminal aparecerá en la otra

---

## Bloque 7: Redes

### 32. Comprueba la conectividad con el servidor google.com enviando unos pocos paquetes.

```bash
ping -c 4 google.com
```

**Nota:** `-c 4` limita a 4 paquetes

### 33. Muestra la configuración de tus interfaces de red.

```bash
ip a
```

**Alternativa:**
```bash
ip addr
```

### 34. Revisa qué puertos están en escucha en tu máquina.

```bash
ss -tuln
```

**Explicación:**
- `-t`: Sockets TCP
- `-u`: Sockets UDP
- `-l`: Solo los que están en escucha (listening)
- `-n`: Muestra números de puerto en lugar de nombres de servicios

### 35. Consulta la dirección IP asociada al dominio google.com.

```bash
host google.com
```

### 36. Realiza la misma consulta de resolución DNS usando otra herramienta distinta.

```bash
dig google.com
```

**Alternativa adicional:**
```bash
nslookup google.com
```

### 37. Conéctate de forma remota a otra máquina mediante un protocolo seguro (si tienes acceso).

```bash
ssh grego@192.168.122.145
```

### 38. Copia un archivo desde tu máquina a otra mediante una conexión remota segura.

```bash
scp grego@192.168.122.145:~/seseion_server.time ~/Escritorio/log_completo.txt
```

---

## Bloque 8: Usuarios y permisos

### 39. Crea un usuario de prueba llamado alumno1.

```bash
sudo useradd -m alumno1
```

**Nota:** `-m` crea el directorio home del usuario

### 40. Cámbiale la contraseña.

```bash
sudo passwd alumno1
```

### 41. Cambia los permisos de un archivo a 755.

```bash
chmod 755 listado.txt
```

**Explicación de 755:**
- 7 (rwx): Propietario puede leer, escribir y ejecutar
- 5 (r-x): Grupo puede leer y ejecutar
- 5 (r-x): Otros pueden leer y ejecutar

### 42. Cambia el propietario de un archivo a otro usuario.

```bash
sudo chown alumno1 listado.txt
```

**Para cambiar propietario y grupo:**
```bash
sudo chown alumno1:alumno1 listado.txt
```

### 43. Elimina el usuario creado.

```bash
sudo userdel -r alumno1
```

**Nota:** La opción `-r` elimina también el directorio home del usuario y su buzón de correo

---
