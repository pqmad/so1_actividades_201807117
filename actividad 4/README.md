# Actividad 4 201807117

## Madeline Perez

### Proceso de instalacion del servicio

Para crear un systemd unit de tipo servicio para ejecutar un script que imprima un saludo y la fecha actual, sigue los siguientes pasos:

El archivo **/myscript.sh** tiene que tener permisos de ejecución. 

1. Guarda el archivo myscript.service en la ruta **/etc/systemd/system/**
2. Recarga la configuración de systemd para que tome en cuenta el nuevo archivo de unidad:
```
systemctl daemon-reload
```

3. Inicia el servicio:
```
systemctl start myscript
```

4. Verifica el estado del servicio:
```
systemctl status myscript
```

Si todo está bien, deberías ver un mensaje que indica que el servicio se está ejecutando.

5. Para asegurarte de que el servicio se inicie automáticamente al arrancar el sistema, usa el siguiente comando:
```
systemctl enable myscript
```

Ahora el servicio se ejecutará automáticamente al iniciar el sistema y cada vez que se inicie manualmente.