# Actividad 3

El problema que se presenta es un error 404 al cargar una URL específica en la aplicación frontend del ejemplo visto en clase. El error se debe a que la configuración del servidor de frontend no está correctamente redirigiendo las rutas al archivo de index.html correspondiente, lo que impide que la aplicación cargue correctamente.

Para solucionar el problema, es necesario modificar la configuración del servidor Nginx que se está utilizando para servir la aplicación frontend. Para ello, se puede crear un archivo llamado default.conf en la carpeta /etc/nginx/conf.d/ dentro del contenedor de Nginx con el siguiente contenido:

```
server {
    listen 80;
    server_name _;
    root /usr/share/nginx/html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

Este archivo de configuración establece que cualquier solicitud que llegue al servidor de Nginx se redirigirá a la ruta correspondiente en el archivo index.html de la aplicación, lo que debería solucionar el error 404 que se está presentando.

Para aplicar estos cambios, es necesario modificar el archivo Dockerfile de la imagen de Nginx para que copie el archivo de configuración en la carpeta correcta. Se puede agregar el siguiente comando al archivo Dockerfile:

```
COPY default.conf /etc/nginx/conf.d/default.conf
```

Con estos cambios, al reconstruir y ejecutar las imágenes de Docker correspondientes, la aplicación frontend debería cargar correctamente sin errores 404 al acceder a cualquier ruta de la aplicación. Además, es importante destacar que estos cambios se realizan sin modificar el código de la aplicación frontend.