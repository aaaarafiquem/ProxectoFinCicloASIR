# FASE DE DESEÑO

## Diagrama de compoñentes do sistema - MotionEye

No caso de MotionEye, o seu creador propón varios escenarios de uso, todos eles recollidos na [súa Wiki](https://github.com/ccrisan/motioneyeos/wiki/Usage-Scenarios). 

### Escenario 1

O primeiro caso que nos mostra é unha simple placa actuando a modo de servidor con MotionEye instalado e unha cámara dalgún tipo. 

Todo esto está interconectado co router da rede local que, se entende, dará saída a Internet. 

**NOTA:** Para poder acceder dende o exterior ó servizo MotionEye é necesario facer un reenvío de portos no router.


![diagrama_motioneye_1](doc/img/diagramas_images/diagrama-un-dispositivo-unha-camara.png)


### Escenario 2

Este segundo caso asemellase ó caso no que desenvolvín o proxecto. Temos múltiples cámaras conectadas ó noso servidor con MotionEye instalado. 

Igual que no caso anterior, interconectado ó router da rede local. Con outro dispositivo dentro da rede que ten acceso ó servidor de streaming.

Como nos comenta o creador, este escenario sería adecuado para sitios onde se poidan montar dúas ou máis cámaras por exemplo, nunha mesma habitación ou habitáculo, tendo en conta que teñen que estar apuntando a diferentes ángulos para cubrir a máxima área posible.

![diagrama_motioneye_2](doc/img/diagramas_images/diagrama-un-dispositivo-multiples-camaras.png)

### Escenario 3

Neste terceiro escenario temos a figura do hub. Que función realiza? Será un dispositivo configurado para xestionar remotamente outros dispositivos MotionEye. Normalmente non teñen cámaras conectadas.

Temos unha configuración local de MotionEye que pode controlar remotamente outras cámaras MotionEye. Poderíamos designar un dos nosos dispositivos correndo MotionEye como **hub** e engadir el todas as outras cámaras baseadas en MotionEye como **Remote motioneye Camera**.

![diagrama_motioneye_3](doc/img/diagramas_images/diagrama-multiples-dispositivos-un-hub.png)

Podemos usar cámaras NON IP con equipos de placa reducida conectados. Por exemplo, unha **cámara de Raspberry Pi** e** unha Raspberry Pi Zero W** co servizo MotionEye instalado:

![diagrama_motioneye_3](doc/img/diagramas_images/rpi_zero_camera.jpg)

### Escenario 4

A diferenza deste escenario do anterior é que o resto de dispositivos úsanse como cámaras de rede simples en lugar de como cámaras motionEye remotas (Remote motioneye Camera).

Se usamos ordenadores de placa reducida como Raspberry Pi ou outras, existe unha función chamada **Fast Network Camera**, é aconsellado habilitala ara ter un rendemento superior.

O servidor terá unha importante carga de traballo por ter que manexar varios servizos de streaming á vez, polo que se recomenda executalo nunha máquina máis potente.

![diagrama_motioneye_4](doc/img/diagramas_images/diagrama-multiples-dispositivos-un-servidor-central.png)

## Diagrama de compoñentes do sistema - Icinga2

Na seguinte imaxe temos os compoñentes de Icinga2:

![icinga2_schema_1](doc/img/diagramas_images/icinga2-schema.jpg)

Neste outro vemos en forma de pequeno esquema os compoñentes e como se conectan entre eles para o seu correcto funcionamento:

![icinga2_schema_2](doc/img/diagramas_images/icinga2-schema-arquitecture.jpg)

No último esquema aquí mostrado, vemos como sería un entorno de monitorización distribuida. O noso escenario non é o suficientemente complexo como para implementar este tipo de configuración. 

En cambio, se temos en mente o suposto de empresa no que en caso de que os clientes requiran ter algún tipo de soporte, si sería convinte ter un servidor central como **zonas master** e cada unha das instalacións dos clientes como **zonas satellite**.


![icinga2_schema_3](doc/img/diagramas_images/icinga2-distribued-monitoring-schema.png)

## Diagrama de rede

No seguinte diagrama de rede podemos ver o escenario real que se realizou neste proxecto. 

Temos 3 ubicacións diferentes:

- **Ubicación 1:** nesta primeira ubicación, teremos a nosa Raspberry Pi actuando de servidor, unha cámara IP e a cámara de Raspberry Pi dentro da mesma rede local. Fixose un reenvío de portos para poder ós servizos dende Internet.
- **Ubicación 2:** na segunda ubicación simplemente temos unha cámara IP, esta ten saída a Internet xa que se fixo o reenvío do porto que utiliza para facer o streaming de vídeo. Engadese no servidor de MotionEye da **ubicación 1**.
- **Ubicación 3:** esta sería calquera ubicación remota que non sexa ningunha das dúas anteriores. O dispositivo pode ser calquera (PC, portátil, móbil, tablet...) con conexión a Internet. Poderá acceder ó servizos de MotionEye e os outros que existan no servidor sen ningún impedimento.


**APUNTE IMPORTANTE:** no caso de ter unha conexión usando tecnoloxía de red móbil (como o caso de Internet por radio que tanto se oferta nas aldeas) non será posible facer o reenvío de portos debido a que á hora de sair a Internet faise baixo un proxy, polo que a IP pública é compartida con máis clientes da compañía con ese mesmo servizo. 

Como este tipo de conexións requiren unha IP localizable, nunca funcionarán. Ainda que o router nos de a opción de facelo, as conexións entrantes "perderanse" no proxy.

Polo que, a alternativa sería conexións de ADSL ou Fibra. O problema é que en moitos sitios non chega a cobertura dese tipo de conexións, polo que en caso de ser imposible cambiar o tipo de conexión a Internet poderíamos probar a facer unha VPN e tratar de reenviar os portos a través dela.

![diagrama_rede](doc/img/diagramas_images/esquema_rede_proxecto.jpg)


## Configuración dos compoñentes

A configuración detallada de todos os compoñentes hardware ou software deste proxecto atópase no [índice](https://gitlab.iessanclemente.net/asirm/a18rebecalb/-/tree/master#índice), no punto nº 5 de implantación.

Todo o que ten que ver ca planificación de tarefas, atópase no punto nº 3 de [planificación](doc/templates/4_planificacion.md).
