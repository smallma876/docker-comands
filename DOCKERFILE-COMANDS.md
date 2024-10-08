# DOCKERFILE COMANDS

- FROM               = PUEDES INDICAR UNA IMAGEN BASE O UN SISTEMA OPERATIVO (WINDOWS, LINUX)
- WORKDIR  /app/    = ubica por defecto en el directorio app del contenedor. 
- COPY  .  /app/   = copia todos los archivos del directorio actual en un directorio app del contenedor.
- ADD http://www.archivos.com/archivos .= copia los archivos de una url al directorio del contenedor, la diferencia con COPY es que puede consultar a una url o tambien un archivo zip.
- RUN npm install = RUN permite ejecutar comandos
- DOCKER HISTORY APP-EJEMPLO = te lista los pasos q se ejecutaron en el dockerfile ademas del tamano de cada paso.
- ENV API https://miapi/ = crea una variable de entorno API
- CMD ["npm", "run", "dev"] = ejecuta el comando sin levantar una nueva shell gastando menos recursos
- CMD npm run dev = ejecuta el comando levantando una nueva shell
- CMD VS RUN = la diferencia es el tiempo de ejecucion RUN cuando se crea las imagenes, CMD cuando se ejecuta el contenedor.
- ENTRYPOINT ["npm", "run", "dev"] = ejecuta el comando.
- CMD vs ENTRYPOINT = cmd puede ser reemplazado si se ejecuta "DOCKER RUN COMANDO" , entrypoint no reemplaza sino agrega como otro parametro.
- EXPOSE 5173 = es netamente informativo, te dice que puerto usar al ejecutar el contenedor.
- USER react = cambia al usuario react

### cuando se crea un usuario debe hacerse al inicio para que pueda ejecutar todo bajo ese usuario.
- COPY --chown = react package*.json = ejecuta el comando bajo el usuario react, algunos comandos necesitan eso si se desea usar otro usuario. Tambien es posible agregar el grupo.
