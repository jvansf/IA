# Pasos para iniciar TensorBoard y Jupyter

Jypyter es un servidor web utilizado para ejecutar sentencias de python y las funciones de tensorflow.

Para ejecutarlos comandos de docker debe abrir el programa "Docker Quickstart Terminal", por medio de comandos debe acceder a la carpeta "TensorFlow con Docker" que esta en el repositorio.

A continuacion encontrara los comandos ultilizados para crear la imagen de docker y el contenedor que incluye las herramientas necesarias para utilizar jupyter y tensorboard.

# Crear un contendor con Jypyter

## Opcion 1: creando la imagen y el contenedor

### 1. Construir la imagen de docker
```
docker build -t tensorflowdemo:1.0 .
```
### 2. Crear un contenedor o mini-pc a partir de la imagen anterior
```
docker run -p 8888:8888 -p 6006:6006 -p 8886:8886 --name tensorflowdemo -it tensorflowdemo:1.0
```
### Iniciar Jupyter dentro del contenedor (Consola No 1)

1. Entrar al contenedor
```
docker exec -i -t tensorflowdemo bash
```
2. Iniciar jupyter notebook en el puerto 8888
```
jupyter notebook
```

### Opcion 2: Usar docker compose

1. Ejecute la sentencia de docker compose como se muestra a continuacion: 
```
docker-compose up --build
```

## TensorBoard 

### Iniciar TensorBoard

Para iniciar tensorBoard dentro del container que contiene jupyter, debe ejecutar los comandos en una nueva consola de docker.

1. Entrar al contenedor
```
docker exec -i -t tensorflowdemo bash
```
2. Iniciar tensorBoard
```
tensorboard --logdir=run1:/tmp/tensorflow/ --port 6006
```

## Acceder a Jupyter y tensorBoard

Verifica la ip generada por docker, luego abre un explorador (Chrome/Mozilla) y entra a la direccion ip:8888, podras comprobar que jupyter esta iniciado.   Para comprobar que tensorBoard esta iniciado, abre nueva pestaña y entra a la direccion ip:6006. Ejemplos:

```
192.168.99.100:8888
192.168.99.100:6006
```


## Descargar una images

Si requiere descargar imagenes para probar los ejemplos, puede utilizar los siguientes comandos:

* wget -r -A pdf,jpg http://images.all-free-download.com/images/graphicthumb/fresh_red_apple_stock_photo_167147.jpg

* mv /notebooks/images.all-free-download.com/images/graphicthumb/fresh_red_apple_stock_photo_167147.jpg apple.jpg

* mv /notebooks/images.all-free-download.com/images/graphicthumb/apple.jpg /notebooks

## Otros comandos de docker

Borrar todos los contenedores

* docker rm $(docker ps -q -f status=exited)

## Debugging python into Visual Studio Code

* [Debug](https://code.visualstudio.com/docs/python/debugging)