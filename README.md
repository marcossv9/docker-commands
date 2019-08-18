# 1. RESUMEN DE COMANDOS DE DOCKER
A continuación un resumen de los comandos más usados de la línea de comandos de Docker.

## 1.1 INFO
Ver la información de docker
```
docker info
```

## 1.2 IMÁGENES
Buscar imágenes de docker
```
docker search <docker_image>
```
Descargar una imagen de docker
```
docker pull <docker_image>
```
Listar todas las imágenes descargadas
```
docker images
```
Borrar imagen
```
docker rmi <docker_image>
```
Borrar todas las imágenes
```
docker rmi -f $(docker images -q)
```
Borrar todas las imágenes huérfanas
```
docker rmi -f $(docker images -q --filter "dangling=true")
```

## 1.3 CREAR CONTENEDOR
Crear un contenedor nuevo (no es necesario tener descargada la imagen de antes. Si no lo está la
descargará automáticamente.)
```
docker run -d --name <nombre_contenedor> -p <puerto_host>:<puerto_docker> -v <host_volume>:<docker_volume> <docker_image>
```

-d: iniciar en docker en modo demonio
--name: nombre del contenedor
--restart=always: para reiniciarlo automáticamente si falla
-v: mapear volúmenes del docker con los del host
-p: mapear puertos

## 1.4 LOGS
Ver los logs
```
docker logs <nombre_contenedor>
```
Ver logs en caliente
```
docker logs -f <nombre_contenedor>
```

## 1.5 CONTENEDORES
Listar todos los contenedores creados
```
docker ps -l
```
Borrar todos los contenedores creados
```
docker rm -f $(docker ps -aq)
```
Borrar todas las configuraciones de docker
```
docker system prune
```
Conectarse a un contenedor
```
docker exec -i -t <nombre_contenedor> /bin/bash
```
Iniciar un contenedor
```
docker start <nombre_contenedor>
```
Parar un contenedor
```
docker stop <nombre_contenedor>
```
Eliminar un contenedor
```
docker rm <nombre_contenedor>
```
Guardar los commits creados
```
docker commit <nombre_contenedor> <docker_image>
```

## 1.6 EXPORTAR/IMPORTAR
Exportar un docker a tar
```
docker export <nombre_contenedor> -o <nombre_contenedor.tar
```
Importar un docker
```
docker import <nombre_contenedor>.tar
```

## 1.7 MONITORIZACIÓN
Memoria, CPU, Networks… en vivo
```
docker stats
```
Procesos de un docker
```
docker top <nombre_contenedor>
```