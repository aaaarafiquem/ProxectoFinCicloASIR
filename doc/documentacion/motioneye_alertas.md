#	CONFIGURACIÓN de ALERTAS de MotionEye

## Instalación e configuración de Postfix

Neste punto configuraremos o envío de alertas para que cada vez que MotionEye detecta movemento nos envíe un correo electrónico.

Primeiro que nada, debemos instalar os paquetes **postfix** e **mailutils**:

`apt-get update && apt-get install postfix mailutils`

![motioneye_alertas_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/1.PNG)

![motioneye_alertas_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/2.PNG)

Unha vez instalados, imos ó ficheiro de configuración do servizo. Copiamos o arquivo **main.cf.proto** e renomeamolo a **main.cf**. Finalmente, deixamolo tal que así (usaremos o comando **cat + unha tubería + grep** para así eliminar os comentarios e os saltos de liña):

`cat /etc/postfix/main.cf | grep -v "^#\|^$"`

![motioneye_alertas_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/3.PNG)

Creamos tamén, o arquivo **sasl_password** (pode ter calquer nome, pero recomendase o por defecto) que sería o arquivo onde resida o nome de usuario e o contrasinal da conta de correo:

![motioneye_alertas_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/4.PNG)

O seguinte paso sería reiniciar o servizo e activar o [Acceso de aplicacións pouco seguras](https://myaccount.google.com/u/4/lesssecureapps):

![motioneye_alertas_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/5.PNG)

Imos agora mandar un correo de proba ó noso propio mail co seguinte comando:

`echo "CORPO DO CORREO" | mail -s "ASUNTO DO CORREO" CorreoDestino`

![motioneye_alertas_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/6.PNG)

Como vemos no log, en principio, mandouse de forma correcta, polo que imos ver se chegou ó correo:

![motioneye_alertas_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/7.PNG)

A continuación, procedemos a configuración no propio MotionEye. 

## Configuración de alertas en MotionEye

Primeiro, debemos activar a opción **Still images** e poñer o **Capture Mode** en **_Motion Triggered_**:

![motioneye_alertas_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/8.PNG)
 
O segundo, activar as notificacións. Cubrimos a información do servidor e a conta SMTP que se vai utilizar. Activamos o cifrado (TLS) e poñemos un nº de segundos que serán as imaxes adxuntas que vai enviar nese lapso de tempo:

![motioneye_alertas_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/9.PNG)

Provocamos movemento diante da cámara e comprobamos no correo de novo...

![motioneye_alertas_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/motioneye_alertas_images/10.PNG)

Finalmente, vemos que si se mandou a alerta coas imaxes pertencentes ós frames onde se detectou o movemento.
