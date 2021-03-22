# Configuración de hosts e servizos en Icinga2

Despois de ter unha instalación exitosa de Icinga2 e IcingaWeb2, o seguinte paso sería engadir hosts e servizos a monitorizar.

Icinga2 monitoriza a súa propia máquina anfitriona por defecto, polo que, xa que temos máis servizos correndo nela, podemos engadir todos eses servizos esenciais a monitorizar.

Tamén podemos engadir algunha das nosas cámaras IP, para que monitorice que se están ou non caídas e o porto polo que traballa o servizo de streaming.

## Engadir servizos 

Icinga2 xa ten varios servizos engadidos por defecto. Estes están declarados no arquivo **/etc/icinga2/conf.d/services.conf**:

![icinga2_config_1](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/1.PNG)

Imos agora facer un pequeno cambio no servizo de SSH que está aquí declarado. Por defecto, o **check_command** do SSH monitoriza polo porto 22. No noso caso, fixemos un cambio de porto, e facemos a conexión a través do **3578**. Polo que revisando a documentación do [check_command by_ssh](https://icinga.com/docs/icinga-2/latest/doc/10-icinga-template-library/#by_ssh) nos Docs oficiais de Icinga observamos o seguinte:

![icinga2_config_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/2.PNG)

Vemos unha variable personalizada que indica o porto, polo que o seguinte paso sería ir de novo o arquivo **services.conf** e engadilo para así á hora de crear os equipos no arquivo **hosts.conf**, poder engadir o porto como variable a monitorizar:

![icinga2_config_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/3.PNG)

No arquivo **hosts.conf**, engadimos a variable ports e indicamos o nº de porto da seguinte maneira:

![icinga2_config_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/4.PNG)

Reiniciamos o servizo de Icinga2 e comprobamos na interface web que está monitorizando polo novo porto de maneira correcta:

![icinga2_config_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/5.PNG)

## Monitorizar servizos web

Ademais do propio IcingaWeb2, podemos monitorizar o resto de páxinas web deste proxecto. Como poden ser o Dashboard de Icinga2 e o MotionEye.

Simplemente descomentamos a esta liña e engadimos o mesmo para o resto de páxinas:

![icinga2_config_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/6.PNG)

Reiniciamos o servizo e comprobamos na interface web:

![icinga2_config_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/7.PNG)


## Monitorizar o servizo de correo

Revisamos cal é o check_command para o servizo de correo no directorio **/usr/lib/nagios/plugins**:

![icinga2_config_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/11.PNG)

Observamos que é **check_mailq**, polo que facemos unha pequena proba do comando:

![icinga2_config_12](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/12.PNG)

Revisamos na documentación do comando que hay un par de argumentos que son obligatorios:

![icinga2_config_13](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/13.PNG)

Agora, imos ó hosts.conf para declarar que imos monitorizar o check_command **check_mailq** cas variables necesarias:

![icinga2_config_14](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/14.PNG)

Revisamos na interface web e vemos que temos a mesma salida que ó executar o comando na consola de comandos:

![icinga2_config_15](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/15.PNG)

## Agregar hosts

Para agregar un novo host, simplemente o engadimos da seguinte maneira no arquivo **hosts.conf**:

![icinga2_config_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/8.PNG)

En xeral, son necesarios os seguintes parámetros:

- Importamos a plantilla de host xenérico
- Poñemos a dirección do host
- Poñemos o check_command desexado, no noso caso un porto tcp
- Poñemos as variables de notificación

Revisamos na interface web e vemos que chegan a eles de forma correcta:

![icinga2_config_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/9.PNG)

Notar que, un dos servizos da cámara remota aparece como **Unhandled**. Isto é porque a cámara IP está capada para non responder as peticións de eco ICMP:

![icinga2_config_16](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/16.PNG)

Sen embargo, si que chega a ela e responde polo porto 554:

![icinga2_config_17](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_config_images/17.PNG)
