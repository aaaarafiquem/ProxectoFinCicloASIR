# REQUIRIMENTOS DO SISTEMA
Este documento describe os requirimentos para RaspbiCCTV especificando que funcionalidade ofrecerá e de que xeito.

## Descrición Xeral

O proxecto é un unha solución xenérica capaz de cubrir distintos casos en canto a videovixilancia se refire, ben sexa á implantación nun ámbito doméstico ou incluso nun máis profesional.

Como se falou no anterior punto, considerase a seguridade como unha das necesidades básicas nesta época na que aumentou e segue crecendo a sensación de inseguridade na poboación, polo que cubriríase cun sistema que, a diferencia da maioría de empresas de seguridade que ofrecen servizos equivalentes, está ó alcance da maior parte da poboación.

É unha solución todo terreo no sentido de que pode ser:
- **Freeware de libre uso**, para que todo o mundo con coñecemento poida despregar o sistema na situación que queira ou necesite.
- **Comercial**, debido a que a maioría de software e hardware utilizado dispón de licenzas GPL, das cales, unha das principais vantaxes é a liberdade de modificación e distribución que da, polo que non é ilegal vender produtos dixitais. Sen embargo, os produtos vendidos deben estar tamén baixo o mesmo tipo de licenza.

O corazón del será a famosa Raspberry Pi, un ordenador de placa única de baixo costo que ten todo o que necesitamos para que funcione como servidor. 

Este servidor conterá o servizo que usaremos para a videovixilancia (MotionEye), o que utilizaremos para a monitorización dos equipos na rede (Icinga2) e o servizo de nube privada para almacenar as nosas imaxes (Owncloud).

Tamén varias cámaras que varían en prezo e tipo.

## Funcionalidades

1. Poder xestionar varios tipos de cámaras e o seu comportamento.
2. Poder xestionar os equipos e servizos para a súa monitorización na rede.
3. Poder xestionar as alertas para o sistema de videovixilancia e o sistema de monitorización.
4. Poder acceder remotamente ás máquinas, ben sexa mediante SSH ou Control remoto.

 
## Requerimentos non funcionais
- Contrasinais robustos.
- Cambio de portos por defecto dos servizos (SSH).
- Reenvío de portos nos routers para acceder fora de rede local.
- Firewall para blindar a rede.
- Antivirus no noso servidor.
- Nome de dominio personalizado para non acceder mediante a nosa ip pública + porto, no caso que sexa necesario.
- Páxinas web seguras coa implementación do protocolo SSL (Certificado Let's Encrypt).


## Tipos de usuarios
Tipos de usuario que poderán acceder ó noso sistema. Poderán diferenciarse polos permisos sobre os datos, pantallas que se lles amosan, operacións que poden levar a cabo, etc.

Usuarios do Sistema Operativo:
- **Usuario administrador:** habilitado con sudo.
- **Usuario para certos servizos:** con permisos para só as carpetas e arquivos dese servizo.

Usuarios de MotionEye:
- **Usuario administrador:** permite acceder a todo o abanico de opcións do sistema, engadir cámaras,
- **Usuario user:** con permisos só para a visualizacióndas cámaras

Usuarios Icinga2:
- **Usuario administrador:** ó ser o usuario administrador ten todos os permisos da aplicación.
- **Usuario monitor:** con permiso para observar o sistema pero non modificar (serían un usuario que tería un cliente no caso de querer ter acceso).

## Avaliación da viabilidade técnica do proxecto

### Hardware requerido
##### Raspberry Pi 3B+

**Por qué Raspberry Pi?**

Porque é, xunto a Arduino, un dos ordenadores de placa única máis famosos e emblemáticos do mercado e posúe as seguintes características:

- Procesador 1,4 GHz
- Conectividade inalámbrica de dobre banda 802.11AC (2.4GHz / 5.0GHz)
- Bluetooth 4.2 
- PoE
- Retrocompatibilidade de aplicacións
- Melloras en la transmisión de vídeo HD a través da rede Wi-Fi
- Garantía de compatibilidade de paquetes en moitos ámbitos.
- Tamaño reducido.


![rpi_esquema](doc/img/produtos/1.png) _**Imaxe explicativa dunha Raspberry Pi 3 Modelo B+**_


Existen varias alternativas no mercado como, por exemplo, a **Rock64** ou **Banana Pi**. Ben é certo que algunhas delas teñen características superiores pero tamén teñen un prezo máis elevado, polo que tendo en conta a filosofía do proxecto e que as características da Raspberry son máis que suficientes para abordalo, este foi elixido como núcleo do proxecto.


![rpi_conectada](doc/img/produtos/2.jpg) _**Imaxe da Raspberry Pi con unha carcasa conectada á rede cun cable RJ45**_

![rpi_parte_traseira](doc/img/produtos/3.jpg) _**Imaxe da parte traseira da Raspberry Pi**_

![rpi_parte_traseira](doc/img/produtos/13.jpg) _**Imaxe da conexión da cámara de Raspberry Pi no porto CSI**_

![rpi_parte_traseira](doc/img/produtos/14.jpg) _**Imaxe comparación de cámara conectada á Raspberry Pi**_

##### Cámaras IP

As escollidas foron a TP-Link Tapo C200 e a Xiaomi 360º 1080p, que contan coas seguntes características en común: 

- Resolución 1080p.
- Detección de movemento.
- Visión nocturna.
- Gran angular de visión (Cabezal con movemento vertical e horizontal 360º).
- Detección de movemento e audio de dobre vía.
- Rañura para tarxeta MicroSD de ata 128 GB ou na nube.
- Dispoñen de app propia para xestionalas.
- Compatibles con Alexa e Google Home.
- Configuración sinxela.

![tp_link_tapo](doc/img/produtos/4.jpg) _**Imaxe da TP-Link Tapo C200**_

<img src="doc/img/produtos/5.jpg"  width="570" height="570"> _**Imaxe da Xiaomi Mi Home 360º 1080p**_

Hai diferentes marcas de cámaras IP e distintos rangos de prezos, sen embargo, escollín estas dúas marcas por ser marcas recoñecidas, por a súa fiabilidade e por o seu prezo accesible. 

Son ideais para interiores xa que contan con unha boa resolución de vídeo ademais dun cabezal que permite ter un ángulo de visión de 360º facendo uso de  e nocturna. Teñen unha app propia para xestionalas dende ela, podemos controlar de maneira independente certas cousas como horario de grabación, alertas, etc.

No noso caso non a imos utilizar máis que para vincular a cámara á nosa rede inalámbrica e para otorgarlles un nome de usuario e contrasinal para que sexa máis seguro.

Algo a ter en conta nas cámaras de Xiaomi é que non veñen preparadas para poder comunicarse a través do protocolo RTSP, só dende a súa propia app Xiaomi Home. De todas maneiras, podemos conseguilo facendo un cambio de firmware, polo que hai que fixarse ben no modelo por se existe un firmware alternativo compatible. Por exemplo, no meu caso, un usuario creou ese firmware e compartiuno ca comunidade [neste repositorio de GitHub](https://github.com/cmiguelcabral/mjsxj05cm-rtsp-server).

Podendo evitar o anterior, o aconsellable sería buscar outros modelos que sí admitan a comunicación polo protocolo RTSP.

**Por qué cámaras IP?**

Porque son moitos dos usuarios non necesitan máis que un par delas, ó ser inalámbricas temos a vantaxe de que non se necesitaría despregar unha gran infraestrutura de cableado e no caso de necesitalos, switches. 

Son intuitivas para os usuarios e fáciles de instalar, poden manipulalas ó seu antollo.

Independentemente de que sexan de marcas diferentes, comportaranse da mesma maneira no noso sistema.

##### Raspberry Pi NoIR Camera Module V2

A cámara oficial para as placas Raspberry Pi é un pequeno módulo que se conecta na rañura CSI das Raspberry Pi.
Conta cas seguintes características:
- Sensor Sony Exmor IMX219 de 8 megapíxeles.
- Modos de video compatibles 1080p30, 720p60 e VGA90.
- Soporta Timelapse e cámara lenta.
- LED inflarroxo, permite a visión nocturna.
- Compatible con todos os modelos de Raspberry Pi (1,2,3,4...) e outros modelos de placas como Arduino.

<img src="doc/img/produtos/6.jpg"  alt="rpi_camera_noir" width="550" height="550"> _**Cámara Raspberry Pi NoIR**_

Como podemos ver, é unha plaquiña que non podemos deixar ó aire libre por posibles estragos, polo que se lle pode poñer unha carcasa como a que vemos nas seguintes fotografías.

![rpi_camera_noir_2](doc/img/produtos/7.jpg) _**Comparación do tamaño da cámara coa carcasa**_

![rpi_camera_noir_3](doc/img/produtos/8.jpeg) _**Cámara montada na súa carcasa**_

### Software
Analizar as opcións software existentes e xustificar a idoneidade dos compoñentes seleccionados.

#### Raspberry Pi OS

**Raspberry Pi OS** (antes coñecido como Raspbian) é unha distribución de GNU/Linux baseada en Debian creada para a arquitectura **armkhf** cuxa última versión foi liberada o 11 de xaneiro de 2021, da actual versión de Debian, Buster.  É unha distro orientada ó aprendizaxe da informática, polo que é moi sinxela, con interface gráfica e varias ferramentas preinstaladas. Podemos facernos coa imaxe deste sistema dende a [páxina oficial de Raspberry Pi](https://www.raspberrypi.org/software/operating-systems/), en calquera das súas versións (con ou sen escritorio). É o sistema operativo recomendado por a Raspberry Pi Fountation.

![rpios_logo](doc/img/produtos/9.jpg)

Existen versións da arquitectura ARM de Sistemas Operativos alternativos das distribucións máis famosas (Debian, CentOS 7...). Sen embargo, como anteriormente se comentou, Raspberry Pi OS, é o sistema operativo recomendado por a Raspberry Pi Fountation, xa que está perfectamente optimizada para os seus dispositivos.

#### MotionEye

**MotionEye** é un frontend web para o demo **Motion** programado en Python. Á súa vez, **Motion** é un software de CCTV para sistemas GNU/Linux. Utiliza a API de captura de vídeo video4linux e podemos utilizar unha gran variedade de dispositivos como:
- Cámaras IP via protocolos RSTP, RTMP e HTTP.
- Cámaras para Raspberry Pi.
- Webcams que utilicen o protocolo V4L2 (video4linux2)
- Tarxetas de captura de vídeo.
- Arquivos de vídeo existentes.

![motioneye_logo](doc/img/produtos/10.png)


Volvendo a MotionEye, vemos que ten unha interface gráfica sinxela ca que podemos configurar todos os aspectos das cámaras, polo que non é necesario ser un usuario experto para poder utilizalo. Incluso existe unha distribución baseada en Debian chamada **MotionEyeOS**, aínda que para este caso, que imos ter outros servizos na mesma máquina para aforrar costes, non é o máis axeitado.

![motioneye_0](doc/img/motioneye_images/0.png)

En todo existen alternativas. Por un lado, atopamos as alternativas gratuitas e OpenSource: ZoneMinder (dispoñible para Linux), Shinobi (multiplataforma) e iSpy (Freeware, só para sistemas Windows). 

Por outra banda, temos Blue Iris que é unha aplicación moi completa e multiplataforma (excepto Linux) pero é de pago, polo que non sería compatible coa nosa metodoloxía.

En resumo, MotionEye foi a escollida porque previamente me chamou a atención Motion, pero facer un bo _frontend_ sería complicado e levaría moito tempo, polo que buscando na rede din co proxecto do usuario de GitHub **ccrisan** creador de MotionEye e que comparte con todo o mundo [no seu repositorio](https://github.com/ccrisan/motioneye).

#### Icinga2

A monitorización de redes é moi importante nestes tempos nos que necesitamos saber se un servidor ou un servizo se viu comprometido ou sufriu unha caída. No noso caso escollín **Icinga2**, un software de monitorización de código aberto. 

![icinga2_logo](doc/img/produtos/11.png)

É un fork do coñecido Nagios no ano 2009. A versión máis recente é a 2.11.8 (decembro de 2020). Icinga2 ademais, conta con unha gran varidade de módulos e plugins creados pola comunidade que axudan a todo o mundo. 

No mercado hai unha amplia gama de aplicacións para este propósito, como Zabbix, Cacti, Centreon, Microsoft Network Monitor... 

**Por que Icinga2?** Ademais de porque é libre e gratuita, está en continuo desenvolvemento con unha gran comunidade detrás reportando e resolvendo erros. Funciona sobre módulos, polo que se necesitamos algunha funcionalidade a maiores, só temos que instalar ese módulo, por exemplo un módulo de análise de datos e gráficas como pode ser PNP.

![icinga2_pnp4nagios](doc/img/produtos/12.jpg)

Por último, pero non menos importante, teño coñecemento e interés na instalación e configuración desta aplicación, polo que me resultará máis sinxelo desenvolver esta tarefa.

## Análise de riscos e interesados
Determinar todas aquelas persoas, entidades ou cousas que poden ter un impacto (positivo ou negativo) no proxecto ou na idea de negocio, e indicar as medidas a levar a cabo para tratar de potenciar os impactos positivos e evitar ou mitigar os posibles impactos negativos.

## Actividades
Definir, de forma xeral, os pasos que se han seguir para levar a cabo o proxecto, de forma que na fase de planificación nos sirvan como referencia para detallar as tarefas, recursos e temporalización necesaria para cada fase.

1.  Análise do entorno no que imos implementar o sistema.
2.  Elección dos produtos que se van utilizar.
3.	Instalación e configuración de Raspberry Pi OS.
4.	Instalación e configuración de MotionEye e Icinga2.
5.	Creación e xestión de alertas no sistema.
6.	Xestión de nome de dominio e reenvío de portos.


## Melloras futuras

Este proxecto está centrado en cubrir unha necesidade que moita xente ten e non se pode permitir. No futuro, podemos engadir novas funcionalidades, como por exemplo:
- Integrar un sistema de alarma co sistema clásico de chaveiros con sensores RFID nunha placa Arduino.
- Integrar varios tipos de sensores (fume, humidade, sonido...).
- Crear un frontend propio para así poder decidir o rumbo que vai tomar e poder integrar todo o anterior sen depender de ninguén.
- Adquisición dun bo servidor central e un servizo de hosting profesional.
