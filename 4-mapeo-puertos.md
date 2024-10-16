# Mapeo de puertos
El mapeo de puertos es un mecanismo que permite redirigir el tráfico de red desde un puerto en el host (tu máquina local o servidor) hacia un puerto específico en un contenedor Docker.
Por ejemplo, supongamos que tienes un contenedor que ejecuta un servidor web en el puerto 80 dentro del contenedor, pero quieres acceder a ese servidor desde tu navegador en la máquina host. Puedes usar el mapeo de puertos para redirigir el tráfico del puerto 80 del contenedor al puerto 3000 en el host. De esta manera, cuando accedas a http://localhost:3000 en tu navegador, el tráfico se dirigirá al servidor web dentro del contenedor en el puerto 80.

![mapeo](img/mapeoPuertos.PNG)

### Para crear un mapeo de puertos (puerto host y puerto contenedor)
El mapeo de puertos se especifica al ejecutar un contenedor Docker utilizando la opción -p o --publish seguida de los puertos que deseas mapear
```
docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>

```
Crear un contenedor a partir de la imagen nginx version alpine con el mapeo de puertos del ejemplo gráfico, host 3000 y contenedor 80
# COMPLETAR
<pre>
PS C:\Users\johana> docker run -d --name contenedor_p1 -p 3000:80 nginx:alpine                                          
55bfefbf2098f670803621f5ea436a9ea1ece5612760cf7ee1920ac6c1c55950
  
</pre>
# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:3000

![image](https://github.com/user-attachments/assets/690074c6-95a7-4d09-8c70-351fc846d9eb)

### Para mapear más de un puerto

```
docker run -d --name <nombre contenedor> -p <puerto host 01>:<puerto contenedor 01> -p <puerto host 02>:<puerto contenedor 02> <nombre imagen>:<tag>
```

Crear un contenedor a partir de la imagen rabbitmq version management-alpine, para este mapeo de puertos usar en el host los mismos puertos del contenedor.
# COMPLETAR
<pre>
Descarga la imagen
PS C:\Users\johana> docker pull  rabbitmq:management-alpine         
management-alpine: Pulling from library/rabbitmq                     
43c4264eed91: Already exists
bf55fc537329: Pull complete
9657c5f3b83f: Pull complete
27abce07d6a1: Pull complete
a1f6e1c8fa85: Pull complete
8f10dd288b86: Pull complete
36d87ab1cf14: Pull complete
fad9de59df01: Pull complete
c1ecdde64545: Pull complete
74f63c251bb2: Pull complete
Digest: sha256:2caa2f2d6ae060624231c8d48b4b1ae6ed8799f4bd709f993ad97a15e3f1cd39
Status: Downloaded newer image for rabbitmq:management-alpine
docker.io/library/rabbitmq:management-alpine
</pre>

<pre>
Basados en la documentación de la imagen rabbitmq en la version management los puertos a utilizarse son 5672 y 15672

PS C:\Users\johana>docker run -d --name contenedor_rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management-alpine
c5e4ceb65ae519949d8f79a9fb094dbfd65c54eee7fc0c2e4338e3e4b5b4dc16

 </pre>
