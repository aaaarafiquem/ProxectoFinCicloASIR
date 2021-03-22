#	INSTALACIÓN de MotionEye

## Credenciais de acceso a MotionEye

Para acceder imos á páxina dedicada no proxecto de [MotionEye](https://raspbicctv.ga/motioneye/).

**Usuario administrador**
- **Nome usuario:** admin
- **Contrasinal:** t&Y(:dGM4Ds+VxfL

**Usuario normal**
- **Nome usuario:** user
- **Contrasinal:** RaspbiContrasinal123.

## Instalación 

Realizar a instalación de MotionEye é moi sinxelo, ademais de que se fai en escasos minutos.

O primeiro paso é instalar a colección de software **ffmpeg**, unha colección de software libre para poder grabar, convertir e facer streaming de audio e vídeo, ademais de varias dependencias:

`# sudo apt-get install ffmpeg libmariadb3 libpq5 libmicrohttpd12`

![motioneye_1](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/1.PNG)

Descargamos o repositorio de Github:

`# wget https://github.com/Motion-Project/motion/releases/download/release-4.2.2/pi_buster_motion_4.2.2-1_armhf.deb`

![motioneye_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/2.PNG)

Instalamos Motion:

`# dpkg -i pi_buster_motion_4.2.2-1_armhf.deb`

![motioneye_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/3.PNG)

Instalamos máis dependencias dos repositorios:

`# apt-get install python-pip python-dev libssl-dev libcurl4-openssl-dev libjpeg-dev libz-dev`

![motioneye_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/4.PNG)

Instalamos agora MotionEye:

`# pip install motioneye`

![motioneye_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/5.PNG)

Creamos el directorio de configuración:

`# mkdir -p /etc/motioneye`

`# cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf`

![motioneye_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/6.PNG)

Creamos también, el directorio para los archivos:

`# mkdir -p /var/lib/motioneye`

Agregamos o script para configurar o demonio ó inicio:

`# cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service`

![motioneye_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/7.PNG)

`# systemctl daemon-reload`

`# systemctl enable motioneye`

`# systemctl start motioneye`

![motioneye_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/8.PNG)

Comprobamos se hai novas actualizacións:

`#  pip install motioneye --upgrade`

`#  systemctl restart motioneye`

![motioneye_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/9.PNG)

Por último, abriremos o porto polo que se comunica MotionEye, o 8765:

![motioneye_12](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/12.PNG)

Una vez feito, imos a http://ip_do_server:8765 e vemos a páxina de login:

![motioneye_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/10.PNG)

E temos a interface lista, lembrar cambiar o contrasinal, xa que por defecto o usuario é **admin** sen contrasinal:

![motioneye_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/11.PNG)

Como desexamos que funcione sobre **https** iremos ó noso VirtualHost e faremos as configuracións necesarias para as redireccións **de http a https**.

Tamén se redireccionará o tráfico de https://raspbicctv.ga ó MotionEye directamente.

![motioneye_13](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/13.PNG)

![motioneye_14](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_images/14.PNG)




