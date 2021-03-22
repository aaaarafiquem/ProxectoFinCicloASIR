# Funcionamento de MotionEye

Neste punto explicarase o funcionamento do núcleo deste proxecto, MotionEye.

Unha vez que o temos instalado, iniciamos sesión como usuario administrador cas credenciais por defecto: 
- **Usuario:** admin
- **Contrasinal:** vacío

Unha vez feito vemos un numeroso abanico de opcións dispoñibles, pero antes, necesitamos engadir unha nova cámara.

## Engadir cámaras

Para iso imos arriba á esquerda e facemos clic no despregable. Seleccionamos a opción **add camera...**:

![funcionamento_motioneye_1](doc/img/funcionamento_motioneye_images/7.JPG)

Ten varios tipos de cámaras para engadir:

- **Local V4L2 Camera:** son cámaras que están conectadas directamente ó sistema motionEye, normalmente a través de USB. 
- **Local MMAL Camera:** son cámaras conectadas directamente ó sistema coma no caso anterior. Sen embargo, diferencianse en que, en lugar de estar conectadas por USB, están específicamente conectadas a través da placa.
- **Network Camera:** son cámaras IP, son dispositivos que transmiten de xeito nativo vídeos polos protocolos RTSP ou MJPEG ou imaxes JPEG sinxelas.
- **Remote motioneye Camera:** son cámaras instaladas noutro servidor MotionEye. Engadindoas aquí, poderemos velas e xestionalas de xeito remoto. 
- **Simple MJPEG Camera:** ó engadir o dispositivo como unha simple cámara MJPEG en lugar de como unha cámara IP mellorará a velocidade de fotogramas. Sen embargo, non estará dispoñible para ela detección de movemento, captura de imaxes nin gravación de películas, o que non é moi convinte para o noso propósito. A cámara debe ser accesible tanto para o servidor como para o seu navegador.

Se queremos engadir unha cámara IP, simplemente necesitamos saber a súa dirección e, en caso de ter credenciais, poñer as correctas:

![funcionamento_motioneye_2](doc/img/funcionamento_motioneye_images/8.JPG)

Neste exemplo, imos engadir a cámara de Raspberry Pi. Dado que non é unha cámara IP, a opción correcta **sería Local MMA Camera**. Despois, só teremos dispoñible a opción **VideoCore Camera**:

![funcionamento_motioneye_3](doc/img/funcionamento_motioneye_images/9.JPG)

Unha vez que demos clic en OK, teremos a cámara engadida:

![funcionamento_motioneye_4](doc/img/funcionamento_motioneye_images/10.JPG)

## Opcións do servizo

Despois de engadir cámaras, podemos observar moitas opcións de configuración:

- Preferencias
- Parámetros xerais

![funcionamento_motioneye_5](doc/img/funcionamento_motioneye_images/1.JPG)

- Dispositivos de vídeo
- Almacenamento de arquivos

![funcionamento_motioneye_6](doc/img/funcionamento_motioneye_images/2.JPG)

- Superposición de texto
- Video Streaming
- Still Images

![funcionamento_motioneye_7](doc/img/funcionamento_motioneye_images/3.JPG)

- Películas

![funcionamento_motioneye_8](doc/img/funcionamento_motioneye_images/4.JPG)

- Detección de Movemento (Motion)
- Notificacións de Movemento

![funcionamento_motioneye_9](doc/img/funcionamento_motioneye_images/6.JPG)

- Días de funcionamento

![funcionamento_motioneye_10](doc/img/funcionamento_motioneye_images/5.JPG)

Todas as opcións dispoñibles son moi intuitivas, polo que non hai nada que resaltar.

