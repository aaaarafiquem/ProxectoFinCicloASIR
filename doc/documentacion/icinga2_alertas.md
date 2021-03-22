# CONFIGURACIÓN de ALERTAS de Icinga2

Neste punto configuraremos o envío de alertas para que cada vez que en Icinga2 pase algún evento crítico nos notifique a través dun correo electrónico.

Tendo en conta a configuración do punto anterior, [a configuración de alertas de MotionEye](/doc/documentacion/motioneye_alertas.md), agora simplemente teremos que facer cambios nos arquivos de configuración de Icinga2.

Hai unha serie de arquivos que son indispensables á hora de facer a configuración, están ubicados no directorio **/etc/icinga2/conf.d/** son:

- users.conf
- notifications.conf
- hosts.conf

Paralelamente, tamén son importantes os ubicados no directorio **/etc/icinga2/scripts/**:

- mail-host-notification.sh
- mail-service-notification.sh

## Arquivo users.conf

É necesario ter un ou máis usuarios e/ou grupos de usuarios que serán notificados en caso dalgún problema. Estes usuarios deben ter definidos todos os atributos personalizados que se usarán cando o comando de notificación se execute.

No contido por defecto do ficheiro **/etc/icinga2/conf.d/users.conf** podemos observar como está declarado o usuario administrador, chamado **icingaadmin** pertencente ó grupo de usuarios **icingaadmins**. Os parámetros de configuración establecen que só recibirá unha notificación sobre problemas **CRÍTICOS** e de **ADVERTENCIAS**. Ademais, enviaranse notificacións de recuperación dos equipos ou servizos despois dunha caída. 

**NOTA:** se non indicamos ningún atributo de configuración de estados e tipos para os usuarios, enviaranse notificacións para todos eles.

![icinga2_alertas_1](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/1.PNG)

Esta mesma configuración podemos atopala tamén na interface web.

No apartado **Contacts**, vemos o noso usuario **icingaadmin** co mesmo nome e correo indicado no ficheiro:

![icinga2_alertas_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/2.PNG)

Vemos que no apartado **ContactGroups** está o usuario que nomeamos anteriormente como membro:

![icinga2_alertas_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/3.PNG)

## Arquivo notifications.conf

O seguinte arquivo a comprobar sería o **notifications.conf**. 

![icinga2_alertas_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/4.PNG)

Para crear obxectos de notificación utilízase a palabra **apply**. Podemos tamén, engadir o atributo user_groups cunha lista de grupos de usuarios ao obxecto Notification. Desta maneira, Icinga 2 enviará notificacións a todos os membros dese grupo. 

## Arquivo hosts.conf

Aquí vemos un exemplo con dúas das nosas cámara, engadindo só a seguinte liña:

`vars.notification["mail"] = {
    groups = [ "icingaadmins" ]
  }`

![icinga2_alertas_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/5.PNG)

Poderemos recibir notificacións sobre o host indicando o grupo de usuarios ou os usuarios de forma explícita.

## Arquivo mail-host-notification.sh e mail-service-notification.sh

Estes son os scripts que van facer o traballo de mandar o correo co seu formato. O bo disto é que poderemos modificalo según as nosas necesidades.

Cos scripts por defecto, as notificacións por mail serían tal que así:

![icinga2_alertas_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/6.PNG)

Cumplen coa súa función, pero son bastante toscas e moi pouco intuitivas visualmente. Coñecendo a comunidade de usuarios de Icinga2, cunha búsqueda rápida pola rede din cunha plantilla HTML que embelece as alertas por correo do usuario de GitHub **shyamjos**. O script está [neste repositorio](https://github.com/shyamjos/HTML-email-template-for-Icinga-2) do seu GitHub e tamén temos unha breve explicacion e vista previa [na súa páxina web](https://shyamjos.com/icinga2-html-template/).

## Instalación das plantillas HTML

A instalación das plantillas non pode ser máis sinxela que substituír as antigas polos scripts de **shyamjos**. 

Facemos antes unha copia dos arquivos orixinales en caso de que algo vaia mal:

![icinga2_alertas_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/9.PNG)

Se observamos unha parte do script, vemos que podemos tamén cambiar ó noso gusto as variables e o texto que estaría no corpo do correo:

![icinga2_alertas_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/10.PNG)

Lembrar darlle permisos de execución os novos scripts, senón daría erro de permisos como podemos ver nos logs:

![icinga2_alertas_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/11.PNG)

Damos entón, permisos de execución a ambos arquivos:

![icinga2_alertas_12](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/12.PNG)

E revisamos de novo que si envía a alerta nos logs:

![icinga2_alertas_13](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/13.PNG)

Despois, comprobamos no correo se chegou correctamente:

![icinga2_alertas_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/7.PNG)

Finalmente, de facer un par de cambios, traducimos o texto do corpo do correo ó galego e quedaría desta maneira.

![icinga2_alertas_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_alertas_images/8.PNG)
