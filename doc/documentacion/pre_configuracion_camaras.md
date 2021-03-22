# Configuración previa das cámaras

Antes de poder engadir as cámaras a MotionEye, debemos facer unha pequena **configuración inicial**.

Neste punto explicarase brevemente os pasos a seguir tanto ca **cámara de Raspberry Pi** como ca **cámara IP TP-Link C200**.

## Cámara de Raspberry Pi

O primeiro paso sería conectala na nosa Raspberry Pi, no **porto CSI** para cámaras:

![rpi_parte_traseira](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/produtos/13.jpg) 
E montar de novo a carcasa da Raspberry:

![rpi_parte_traseira](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/produtos/14.jpg) 

Por último, debemos ir á **Configuración de Raspberry Pi**:

![rpi_config](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/1.PNG)

E activamos na xanela de **Interfaces** a opción **Cámara**:

![rpi_config_camara](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/2.PNG)

## Cámara de TP-Link C200

O primeiro paso é descargar a aplicación na **Play Store** ou **App Store**, dependendo do móbil que teñamos.

Ó abrila temos unha interface coma esta:

![tp_link_config_camara](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/3.jpg)

Tocamos o botón de arriba a dereita con un símbolo + para engadir unha nova cámara e pasaremos a este menú para elixir o noso modelo:

![tp_link_config_camara_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/4.jpg)

Ó revisar cal é o noso modelo e tocar no correcto, teremos que facer o proceso de sincronización **ca nosa rede Wifi**.

Destacar que este tipo de aparellos **só funciona en conexións Wifi 2.4 GHz** polo que se non está segmentado haberá que habilitalo na configuración do router.

Omitimos o proceso de sincronización, xa que é indicar a que rede se vai conectar e poñer as credenciais...

![tp_link_config_camara_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/5.jpg)

Unha vez sincronizada podemos tocar na cámara e teremos algo coma esto:

![tp_link_config_camara_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/6.jpg)

Facemos clic no engranaxe que se encontra arriba á dereita e teremos como resultado un menú coma o seguinte. 

![tp_link_config_camara_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/11.jpg)

Ó facer clic na primeira opción cunha miniatura da imaxe e o nome que lle demos á cámara, levaranos a outro menú. 

Nel observamos algúns **datos interesantes** como a **dirección IP** otorgada, a **dirección MAC**, a **versión do firmware** entre outros:

![tp_link_config_camara_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/7.jpg)

Volvendo ó menú anterior, se baixamos un pouco máis imos ir á opción **Configuración avanzada**:

![tp_link_config_camara_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/8.jpg)

Aquí temos a opción **Cuenta de cámara**:

![tp_link_config_camara_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/9.jpg)

 Esto permitiranos otorgar un nome de usuario e un contrasinal para poder acceder ó protocolo RTSP:

 ![tp_link_config_camara_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/10.jpg)

Despois necesitaríamos saber cal sería a **dirección de onde sacará o streaming de imaxe**. Para isto iremos á base de datos de cámaras que encontramos na [web de iSpy](https://www.ispyconnect.com/cameras#google_vignette). Buscaremos a marca e modelo da nosa cámara, completamos cos datos correctos e xeraranos a dirección correcta:

 ![tp_link_config_camara_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/12.JPG)

Podemos probar que funciona dende o **reproductor VLC**:

 ![tp_link_config_camara_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/confi_camaras_images/13.jpg)

Unha vez que temos esto feito, pasaremos ó seguinte punto...
