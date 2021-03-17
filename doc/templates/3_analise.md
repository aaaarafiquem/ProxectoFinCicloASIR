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

1.	Instalación e configuración de Raspberry Pi OS.
2.	Instalación e configuración de MotionEye, Icinga2.
3.	Xestión de cámaras.
4.	Xestión de hosts e servizos de monitorización.
5.	Creación e xestión de alertas.
6.	Xestión de nome de dominio.
7.	Control remoto de máquinas.
 
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
- Tamaño reducido

Existen varias alternativas no mercado como, por exemplo, a **Rock64** ou **Banana Pi**. Ben é certo que algunhas delas teñen características superiores pero tamén teñen un prezo máis elevado, polo que tendo en conta a filosofía do proxecto e que as características da Raspberry son máis que suficientes para abordalo, este foi elixido como núcleo do proxecto.

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

- Raspberry Pi OS
- MotionEye
- Icinga2

## Análise de riscos e interesados
Determinar todas aquelas persoas, entidades ou cousas que poden ter un impacto (positivo ou negativo) no proxecto ou na idea de negocio, e indicar as medidas a levar a cabo para tratar de potenciar os impactos positivos e evitar ou mitigar os posibles impactos negativos.

## Actividades
Definir, de forma xeral, os pasos que se han seguir para levar a cabo o proxecto, de forma que na fase de planificación nos sirvan como referencia para detallar as tarefas, recursos e temporalización necesaria para cada fase.

## Melloras futuras
É posible que o noso proxecto se centre en resolver un problema concreto que se poderá ampliar no futuro con novas funcionalidades, novas interfaces, etc.
