# docker-comands
Comandos de docker

## sobre imagenes

- docker build -t app-react . = crea la imagen basado en el dockerfile y con punto al final porq es la ruta del dockerfile
- docker build -t app-react:1 . = crea la imagen con una tag 1
- docker image ls      = listar imagenes
- docker image prune = elimina imagenes que no se usen

## correr el contenedor

- docker run -it ubuntu = ejecutar contenedor de forma interactica, "exit" para salir de la terminal interactiva.
- docker run -it app-react = corre la imagen, -i mantiene entrada abierta para comunicarte con el contenedor, -t emula un terminal.
- docker run -t app-react sh = corre la image interactivamente indicandole una shell en este caso sh
- docker run -d --name holarun app-react:2 = correr el contenedor y crear el nombre en una linea, ademas -d no muestra consola.
- docker run -d -p 80:5173 --name holarun e74 = crea y corre un contenedor con los puertos 80(anfitrion) y 5173(contenedor) 
- docker run -d -p 3000:3000 -v datos:/app/datos app-react:3 = crea y ejecuta un contenedor con volumen de nombre datos con la ruta dentro del contenedor /app/datos. Lo malo es que el duenio del volumen es root. 
- docker create app-react:2 = crea un contenedor en base a una imagen con su tag, solo crea no ejecuta.
- docker create --name holamundo app-react:2 = crea el contenedor con nombre.
- docker start holamundo = inicia contenedor holamundo.

## volumenes

- docker volume ls = lista volumenes
- docker volume rm  nombrevolumen = elimina volumen
- docker volume create datos = crea un volumen llamado datos
- docker volume inspect datos = inspecciona el volumen datos

## borrar imagenes o contenedores

- docker image prune = elimina imagenes que no se usen
- docker image rm 073 bd0 e6c = borra las imagenes 073 bd0 e6c
- docker image remove app-react:1 = borra la imagen especificada con el tag.
- docker container prune = elimina contenedores que no se usan

## logs del contenedor

- docker logs holamundo = ver los logs del contenedor holamundo, tambien puede ser el id en ves del nombre.
- docker logs -f holamundo = mira los logs y no nos devuelve la terminal
- docker logs -n 5 holamundo = mira los logs solo 5 lineas
- docker logs -t -n 10 holamundo = muestra los logs con el timestamp y 10 lineas

## listar contenedores

- docker ps                = listar contenedores corriendo
- docker ps -a           =  listar contenedores detenidos y corriendo

## detener contenedores

- docker stop hashImagen(3 primeros caracteres) = para detener un contenedor
- docker stop 3c2 = detener el contenedor con el id 3c2, tambien puede ir el nombre.

## administracion de imagenes

- docker image save -o app-react.tar nschurmann/app-react:3 = comprime imagen en un archivo app-react.tar
- docker image load -i app-react.tar = vuelve a cargar la imagen desde el archivo tar, se usa para compartir imagenes.
- docker push nschurmann/app-ejemplo:2 = sube la imagen a docker hub
- docker login = permite logearse 
- docker exec -it holamundo sh = permite ingresar al contenedor a ejecutar comandos de manera interactiva, sh es el tipo de shell en este caso es sh por la distro de linux alpine.
- docker exec holamundo ls = ejecuta el comando ls directamente y devuelve lista de archivos.

