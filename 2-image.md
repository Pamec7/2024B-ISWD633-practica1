# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 
# COMPLETAR 

<pre>La relación entre una imagen y un contenedor es que la imagen actúa como la plantilla o el archivo base que contiene todo lo necesario para que una aplicación funcione, mientras que el contenedor es la instancia en ejecución de esa imagen. Es decir, el contenedor utiliza la imagen para ejecutar la aplicación en un entorno aislado</pre>

![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
# COMPLETAR

<pre>
PS C:\Users\johana> docker pull hello-world   
Using default tag: latest
latest: Pulling from library/hello-world
Digest: sha256:d211f485f2dd1dee407a80973c8f129f00d54604d2c90732e8e320e5038a0348
Status: Image is up to date for hello-world:latest
docker.io/library/hello-world:latest
</pre>

**¿Qué es nginx?**
# COMPLETAR 
<pre>Nginx es un servidor web y actúa como intermediario entre los usuarios y otros servidores (proxy inverso).Nginix entrega contenido web y distribuye el tráfico de red de forma eficiente. Optimiza el rendimiento, balancea la carga entre servidores y mejora la seguridad. Además, es muy utilizado por su capacidad de manejar múltiples conexiones simultáneas en aplicaciones de alto tráfico.</pre>

Descargar la imagen  **nginx** en la versión **alpine**
# COMPLETAR
<pre>PS C:\Users\johana> docker pull nginx:alpine          
alpine: Pulling from library/nginx
43c4264eed91: Pull complete
d1171b13e412: Pull complete
596d53a7de88: Pull complete
f99ac9ba1313: Pull complete
fd072e74e282: Pull complete
379754eea6a7: Pull complete
45eb579d59b2: Pull complete
472934715761: Pull complete
Digest: sha256:2140dad235c130ac861018a4e13a6bc8aea3a35f3a40e20c1b060d51a7efd250
Status: Downloaded newer image for nginx:alpine
docker.io/library/nginx:alpine

</pre>

### Listar imágenes

```
docker images
```

# COLOCAR UNA CAPTURA DE PANTALLA DEL RESULTADO 
![image](https://github.com/user-attachments/assets/2674e52f-54e2-4cb6-b192-27ae09747b4d)

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
# COMPLETAR
<pre>
PS C:\Users\johana> docker inspect hello-world    
[                                      
    {
        "Id": "sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a",
        "RepoTags": [
            "hello-world:latest"
        ],
        "RepoDigests": [
            "hello-world@sha256:d211f485f2dd1dee407a80973c8f129f00d54604d2c90732e8e320e5038a0348"
        ],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2023-05-02T16:49:27Z",
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/hello"
            ],
            "ArgsEscaped": true,
            "Image": "",
            "Volumes": null,
            "WorkingDir": "/",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 13256,
        "GraphDriver": {
            "Data": {
                "MergedDir": "/var/lib/docker/overlay2/31b9ddc030db943dccd1192aa9e82a831f976e0e5f7fa62d910491beaff8a8c4/merged",
                "UpperDir": "/var/lib/docker/overlay2/31b9ddc030db943dccd1192aa9e82a831f976e0e5f7fa62d910491beaff8a8c4/diff",
                "WorkDir": "/var/lib/docker/overlay2/31b9ddc030db943dccd1192aa9e82a831f976e0e5f7fa62d910491beaff8a8c4/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:ac28800ec8bb38d5c35b49d45a6ac4777544941199075dff8c4eb63e093aa81e"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]

</pre>

**¿Con qué algoritmo se está generando el ID de la imagen**
# COMPLETAR
<pre>
  El ID de la imagen hello-world se genera utilizando el algoritmo SHA-256.
  "Id": "sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a"
</pre>

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
# COMPLETAR
<pre>
PS C:\Users\johana> docker rmi hello-world          
Untagged: hello-world:latest
Untagged: hello-world@sha256:d211f485f2dd1dee407a80973c8f129f00d54604d2c90732e8e320e5038a0348
Deleted: sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a
Deleted: sha256:ac28800ec8bb38d5c35b49d45a6ac4777544941199075dff8c4eb63e093aa81e

</pre>

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

