# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
# COMPLETAR
<pre>
  PS C:\Users\johana> docker create --name srv-web nginx:alpine                      
a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1 
</pre>

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
# COMPLETAR
<pre>
PS C:\Users\johana> docker create hello-world                
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete
Digest: sha256:d211f485f2dd1dee407a80973c8f129f00d54604d2c90732e8e320e5038a0348
Status: Downloaded newer image for hello-world:latest
ff8ae4fffb47e27e4b5e94b2ad45c9c4abdfcee100be27e4e30a81b253985099
</pre>

### Listar los contenedores ejecutándose o no

```
docker ps -a
```

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
# COMPLETAR
<pre>
  PS C:\Users\johana> docker start srv-web                    
  srv-web
</pre>

### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](img/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR
<pre>
PS C:\Users\johana> docker run --name srv-web2 nginx:alpine 
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/10/16 17:11:10 [notice] 1#1: using the "epoll" event method
2024/10/16 17:11:10 [notice] 1#1: nginx/1.27.2
2024/10/16 17:11:10 [notice] 1#1: built by gcc 13.2.1 20240309 (Alpine 13.2.1_git20240309)
2024/10/16 17:11:10 [notice] 1#1: OS: Linux 5.15.153.1-microsoft-stansoft-standard-WSL2
2024/10/16 17:11:10 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/10/16 17:11:10 [notice] 1#1: start worker processes
2024/10/16 17:11:10 [notice] 1#1: start worker process 30
2024/10/16 17:11:10 [notice] 1#1: start worker process 31
2024/10/16 17:11:10 [notice] 1#1: start worker process 32
2024/10/16 17:11:10 [notice] 1#1: start worker process 33
2024/10/16 17:11:10 [notice] 1#1: start worker process 34
2024/10/16 17:11:10 [notice] 1#1: start worker process 35
2024/10/16 17:11:10 [notice] 1#1: start worker process 36
2024/10/16 17:11:10 [notice] 1#1: start worker process 37
2024/10/16 17:11:10 [notice] 1#1: start worker process 38
2024/10/16 17:11:10 [notice] 1#1: start worker process 39
2024/10/16 17:11:10 [notice] 1#1: start worker process 40
2024/10/16 17:11:10 [notice] 1#1: start worker process 41
2024/10/16 17:11:10 [notice] 1#1: start worker process 42
2024/10/16 17:11:10 [notice] 1#1: start worker process 43
2024/10/16 17:11:10 [notice] 1#1: start worker process 44
2024/10/16 17:11:10 [notice] 1#1: start worker process 45

</pre>
**¿Qué sucede luego de la ejecución del comando?**
# COMPLETAR  
<pre>
El contenedor de Nginx se inicia y ejecuta un script de entrada que configura el servidor.Una vez se completa la configuración, Nginx comienza a funcionar y se crean múltiples procesos de trabajo para manejar las solicitudes entrantes.
</pre>

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
# COMPLETAR
<pre>
 PS C:\Users\johana> docker run -d --name srv-web3 nginx:alpine                     
522cdcfd49c7028d81ed8ab23c188b14e14d6dc2928ceb6595256c0301b2637e

</pre>
### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR
<pre>
PS C:\Users\johana> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS                     PORTS     NAMES        
522cdcfd49c7   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute          80/tcp    srv-web3     
51e11090b2a0   nginx:alpine   "/docker-entrypoint.…"   7 minutes ago        Exited (0) 2 minutes ago             srv-web2     
ff8ae4fffb47   hello-world    "/hello"                 11 minutes ago       Created                              optimistic_cartwright
a00f0e4dbbf0   nginx:alpine   "/docker-entrypoint.…"   13 minutes ago       Up 9 minutes               80/tcp    srv-web      

PS C:\Users\johana> docker rm optimistic_cartwright
optimistic_cartwright
  
</pre>

Verificar que el contenedor que se eliminó
# COMPLETAR
<pre>

PS C:\Users\johana> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                     PORTS     NAMES
522cdcfd49c7   nginx:alpine   "/docker-entrypoint.…"   3 minutes ago    Up 3 minutes               80/tcp    srv-web3
51e11090b2a0   nginx:alpine   "/docker-entrypoint.…"   9 minutes ago    Exited (0) 4 minutes ago             srv-web2
a00f0e4dbbf0   nginx:alpine   "/docker-entrypoint.…"   15 minutes ago   Up 11 minutes              80/tcp    srv-web

</pre>
### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR
<pre>
PS C:\Users\johana> docker rm -f srv-web3
srv-web3
</pre>

Verificar que el contenedor que se eliminó
# COMPLETAR
<pre>
PS C:\Users\johana> docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS                     PORTS     NAMES
51e11090b2a0   nginx:alpine   "/docker-entrypoint.…"   11 minutes ago   Exited (0) 6 minutes ago             srv-web2
a00f0e4dbbf0   nginx:alpine   "/docker-entrypoint.…"   17 minutes ago   Up 14 minutes              80/tcp    srv-web
  
</pre>

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR
<pre>
PS C:\Users\johana> docker inspect srv-web
[
    {
        "Id": "a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1",
        "Created": "2024-10-16T17:05:20.343522621Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 602,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-10-16T17:08:57.673459841Z",  
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:cb8f91112b6b50ead202f48bbf81cec4b34c254417254efd94c803f7dd718045",
        "ResolvConfPath": "/var/lib/docker/containers/a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1/hostname",
        "HostsPath": "/var/lib/docker/containers/a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1/hosts",
        "LogPath": "/var/lib/docker/containers/a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1/a00f0e4dbbf0c7da292efc0c60772568e588be06a1bd0afac8d8db8d9a2da4f1-json.log",
        "Name": "/srv-web",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                21,
                60
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/50498f3f5a2baca142ffc46444b48725d75ea16a650e443ff4e623b8fe302626-init/diff:/var/lib/docker/overlay2/0b161afd19826ed01dda1fb603e643aab3cb8f2270b58b450e23ad52a58321ed/diff:/var/lib/docker/overlay2/0ab99165d8f9a580364bff0420cdd65bf9faaee07dd48ecca08e0e60ece2acfc/diff:/var/lib/docker/overlay2/6bd4341e5024eefd3753202ad3f57031ac65541ddfe00fe142682c40f0d7c72c/diff:/var/lib/docker/overlay2/be15b0e2f0aeaab071b4eb96153dc1e3848ba76258d9671b2e17a5f8cdca70fd/diff:/var/lib/docker/overlay2/c55e3f8fb468d4e4df2aa5ad2a08ac4758206cf7f97578594be8f06d317492b4/diff:/var/lib/docker/overlay2/c8d4f0879c6637843bf8ec25a3eb722c39f2d6987b52ef0c720c6823d6719c1b/diff:/var/lib/docker/overlay2/44af83974b1095eb472ffd3f55595bc59039edb9090e97c1e933ad6d62afb3df/diff:/var/lib/docker/overlay2/9d03c0d56d6afd81af85d718282bfc82f87021bf01fb31493fa64553285fcf1a/diff",
                "MergedDir": "/var/lib/docker/overlay2/50498f3f5a2baca142ffc46444b48725d75ea16a650e443ff4e623b8fe302626/merged",
                "UpperDir": "/var/lib/docker/overlay2/50498f3f5a2baca142ffc46444b48725d75ea16a650e443ff4e623b8fe302626/diff",
                "WorkDir": "/var/lib/docker/overlay2/50498f3f5a2baca142ffc46444b48725d75ea16a650e443ff4e623b8fe302626/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "a00f0e4dbbf0",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.27.2",
                "PKG_RELEASE=1",
                "DYNPKG_RELEASE=1",
                "NJS_VERSION=0.8.6",
                "NJS_RELEASE=1"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:alpine",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "823d7f139bf09891a225e5d3ba2b32abf37758b733d33f1b4791920ae51d4dde",
            "SandboxKey": "/var/run/docker/netns/823d7f139bf0",
            "Ports": {
                "80/tcp": null
            },
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "5e314c015784eb824c6138f4a3bb01d0d632a3a13a62ed9d3644267a836d28be",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "02:42:ac:11:00:02",      
                    "DriverOpts": null,
                    "NetworkID": "d411cf62f1635ac3b4595ddfdf8b959e840f16d934bee989579fd1aa90984c54",
                    "EndpointID": "5e314c015784eb824c6138f4a3bb01d0d632a3a13a62ed9d3644267a836d28be",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]
</pre>
