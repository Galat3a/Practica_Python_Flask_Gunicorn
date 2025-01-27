# Practica_Python_Flask_Gunicorn

## 1. Despliegue 
Instalamos el gestor de paquetes de Python pip:
``` bash
sudo apt-get update && sudo apt-get install -y python3-pip

```
<img src="./Capturas/1.png">

Instalamos el paquete pipenv para gestionar los entornos virtuales:
``` bash
pip3 install pipenv

PATH=$PATH:/home/$USER/.local/bin
pipenv --version
``` 
<img src="./Capturas/2.png">

Después instalaremos el paquete python-dotenv para cargar las variables de entorno.

``` bash
pip3 install python-dotenv
``` 
Creamos el directorio en el que almacenaremos nuestro proyecto:
``` bash
sudo mkdir -p /var/www/app
sudo chown -R $USER:www-data /var/www/app
sudo chmod -R 775 /var/www/app
``` 