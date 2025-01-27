# Practica_Python_Flask_Gunicorn

## 1. Despliegue 
Instalamos el gestor de paquetes de Python pip:
``` bash
sudo apt-get update && sudo apt-get install -y python3-pip
``` 
Instalamos el paquete pipenv para gestionar los entornos virtuales:
``` bash
pip3 install pipenv

PATH=$PATH:/home/$USER/.local/bin
pipenv --version
``` 
<img src="./Capturas/2.png">
<img src="./Capturas/3.png">

Después instalaremos el paquete python-dotenv para cargar las variables de entorno.

``` bash
pip3 install python-dotenv
``` 
<img src="./Capturas/4.png">

Creamos un directorio y le damos los permisos adecuados

<img src="./Capturas/5.png">

Creamos un fichero .env con el contenido que se indica:

<img src="./Capturas/6.png">

Iniciamos ahora nuestro entorno virtual. Pipenv cargará las variables de entorno desde el fichero .env de forma automática:
``` bash
pipenv shell
 source /home/vagrant/.local/share/virtualenvs/python_ale-qBDe549k/bin/activate
``` 
<img src="./Capturas/8.png">

Crear la aplicación Flask:
<img src="./Capturas/9.png">

Contenido de application.py:
<img src="./Capturas/10.png">

Contenido de wsgi.py:
<img src="./Capturas/11.png">

Corremos la palicacion con el servidor web integrado de Flask:
``` bash
flask run --host '0.0.0.0'
``` 
<img src="./Capturas/12.png">
<img src="./Capturas/13.png">

``` bash
gunicorn --workers 4 --bind 0.0.0.0:5000 wsgi:app
``` 
<img src="./Capturas/14.png">

``` bash
/home/vagrant/.local/share/virtualenvs/python_ale-qBDe549k/bin/gunicorn
``` 

Editamos el archivo:
``` bash
/etc/systemd/system/flask_app.service
``` 
<img src="./Capturas/15.png">
<img src="./Capturas/16.png">

Configuración de Nginx

``` bash
sudo nano /etc/nginx/sites-available/app.conf
```
Comprobacion del link simbolico creado:

<img src="./Capturas/18.png">

Comprobación de que la configuración de Nginx no contiene errores:

<img src="./Capturas/19.png">

Reinicio y comprobación del servicio:

<img src="./Capturas/20.png">

Se edita el archivo /etc/hosts para que asocie la IP de la máquina virtual al servidor.
En Windows está en el siguiente directorio:

``` bash
C:\Windows\System32\drivers\etc\hosts
``` 

Se añade la asociación:

192.168.11.11 pythonapp.izv www.pythonapp.izv

<img src="./Capturas/21.png">

# Tarea