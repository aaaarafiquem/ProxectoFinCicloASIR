#	INSTALACIÓN de MotionEye
**MotionEye** é un frontend web para o demonio Motion programado en Python. Á súa vez, **Motion** é un software de CCTV para sistemas GNU/Linux. Utiliza a API de captura de vídeo video4linux e podemos utilizar unha gran variedade de dispositivos como:
- Cámaras IP via protocolos RSTP, RTMP e HTTP.
- Cámaras para Raspberry Pi.
- Webcams que utilicen o protocolo V4L2 (video4linux2)
- Tarxetas de captura de vídeo.
- Arquivos de vídeo existentes.

Volvendo a MotionEye, vemos que ten unha interface gráfica sinxela ca que podemos configurar todos os aspectos das cámaras. Polo que non é necesario ser un usuario experto para poder utilizalo. Incluso existe unha distribución basada en Debian chamada MotionEyeOS, ainda que para este caso, non é o que máis nos convén.

![motioneye_0](doc/img/motioneye_images/0.png)


## INSTALACIÓN

Realizar a instalación de MotionEye é moi sinxelo, ademais de que se fai en escasos minutos.

O primeiro paso é instalar a colección de software **ffmpeg**, unha colección de software libre para poder grabar, convertir e facer streaming de audio e vídeo, ademais de varias dependencias:

`# sudo apt-get install ffmpeg libmariadb3 libpq5 libmicrohttpd12`

![motioneye_1](doc/img/motioneye_images/1.PNG)

Descargamos o repositorio de Github:

`# wget https://github.com/Motion-Project/motion/releases/download/release-4.2.2/pi_buster_motion_4.2.2-1_armhf.deb`

![motioneye_2](doc/img/motioneye_images/2.PNG)

Instalamos Motion:

`# dpkg -i pi_buster_motion_4.2.2-1_armhf.deb`

![motioneye_3](doc/img/motioneye_images/3.PNG)

Instalamos máis dependencias dos repositorios:

`# apt-get install python-pip python-dev libssl-dev libcurl4-openssl-dev libjpeg-dev libz-dev`

![motioneye_4](doc/img/motioneye_images/4.PNG)

Instalamos agora MotionEye:

`# pip install motioneye`

![motioneye_5](doc/img/motioneye_images/5.PNG)

Creamos el directorio de configuración:

`#  mkdir -p /etc/motioneye`

`# cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf`

Creamos también, el directorio para los archivos:

`# mkdir -p /var/lib/motioneye`

Agregamos o script para configurar o demonio ó inicio:

`# cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service`

`# systemctl daemon-reload`

`# systemctl enable motioneye`

`# systemctl start motioneye`

Comprobamos se hai novas actualizacións:

`#  pip install motioneye --upgrade`

![motioneye_6](doc/img/motioneye_images/6.PNG)

`#  systemctl restart motioneye`

Una vez feito, imos a http://ip_do_server:8765 e vemos a páxina de login:

![motioneye_7](doc/img/motioneye_images/7.PNG)

E temos a interface lista, lembrar cambiar o contrasinal, xa que por defecto o usuario é **admin** sen contrasinal:

![motioneye_8](doc/img/motioneye_images/8.PNG)







