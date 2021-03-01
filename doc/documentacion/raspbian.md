#	INSTALACIÓN e CONFIGURACIÓN BÁSICA de Raspberry Pi OS

**Raspberry Pi OS** (antes coñecido como Raspbian) é unha distribución de GNU/Linux basada en Debian baseada na arquitectura armkhf cuxa última versión foi liberada o 11 de xaneiro de 2021, basada na actual versión de Debian, Buster.  É unha distro orientada ó aprendizaxe da informática, polo que é moi sinxela, con interface gráfica e varias ferramentas preinstaladas. Podemos facernos coa imaxe deste sistema dende a [páxina oficial de Raspberry Pi](https://www.raspberrypi.org/software/operating-systems/), en calquera das súas versións (con ou sen escritorio). É o sistema operativo recomendado por a Raspberry Pi Fountation.

Para a súa instalación, debemos contar con unha Raspberry Pi, unha tarxeta MicroSD e outro equipo para poder flashear a imaxe na MicroSD. 

## Flasheo da imaxe do sistema na tarxeta MicroSD

No meu caso, vou utilizar un software chamado Balena Etcher, podemos descargalo dende a súa [páxina oficial](https://www.balena.io/etcher/).

Primeiro de todo, abrimos o programa e encontramos unha interfaz moi sinxela:

![balena_1](doc/img/rapbian-images/balena-1.PNG)


Escollemos a imaxe que desexamos queimar na MicroSD:

![balena_2](doc/img/rapbian-images/balena-2.PNG)


Como podemos ver, temos a imaxe seleccionada. Agora resta escoller un dispositivo no que queimala:

![balena_3](doc/img/rapbian-images/balena-3.PNG)


Vemos que nos está avisando de que en varias unidades que temos nos está avisando de que son dispositivos con gran capacidade, tamén que son discos do sistema e que un deles é de onde proven a imaxe que estamos a coller:

![balena_4](doc/img/rapbian-images/balena-4.PNG)

Unha vez que temos ambas cousas, só temos que darlle ó botón **Flash!** para que comece o proceso:

![balena_5](doc/img/rapbian-images/balena-5.PNG)

Esperamos a que se complete...

![balena_6](doc/img/rapbian-images/balena-6.PNG)

Unha vez feito, teremos unha pantalla coma esta:

![balena_7](doc/img/rapbian-images/balena-7.PNG)


## Instalación de Raspberry Pi OS

Coa imaxe do sistema flasheada na MicroSD, simplemente a introducimos na Raspberry e enchufamola á corriente e conectarlle unha saída de vídeo (non olvidar como mínimo un teclado e un rato).

O primeiro que nada, temos esta pantalla onde debemos indicar a acción que queremos realizar:

![raspbian_1](doc/img/rapbian-images/1.PNG)


Seleccionamos o idioma que queremos para o sistema:

![raspbian_2](doc/img/rapbian-images/2.PNG)

Agardamos a que carguen todos os compoñentos do CD:

![raspbian_3](doc/img/rapbian-images/3.PNG)

Utilizamos o particionado de disco guiado polo momento:

![raspbian_4](doc/img/rapbian-images/4.PNG)

Seleccionamos o disco no que queremos que se instale o sistema:

![raspbian_5](doc/img/rapbian-images/5.PNG)

Poñemos todo nunha partición:

![raspbian_6](doc/img/rapbian-images/6.PNG)

Revisamos e finalizamos a configuración dos discos:

![raspbian_7](doc/img/rapbian-images/7.PNG)



![raspbian_8](doc/img/rapbian-images/8.PNG)

Esperamos a que se instale o sistema...

![raspbian_9](doc/img/rapbian-images/9.PNG)

Preguntanos se queremos instalar o GRUB, obviamente decimos que si:

![raspbian_10](doc/img/rapbian-images/10.PNG)

Escollemos o único que temos:

![raspbian_11](doc/img/rapbian-images/11.PNG)

Esperamos a que instale...

![raspbian_12](doc/img/rapbian-images/12.PNG)

Finaliza a instalación:

![raspbian_13](doc/img/rapbian-images/13.PNG)

Fai unha limpeza de paquetes da instalación:

![raspbian_14](doc/img/rapbian-images/14.PNG)

Unha vez que reiniciamos, xa temos o noso Raspberry Pi OS co seu escritorio. Observamos que necesitamos configurar un par de cousiñas antes de continuar:

![raspbian_15](doc/img/rapbian-images/15.PNG)

Vemos que nos pregunta polo idioma e franxa horaria do sistema, escollemos:

![raspbian_16](doc/img/rapbian-images/16.PNG)

Cambiamos o contrasinal do usuario por defecto **pi** (que ten o mesmo contrasinal):

![raspbian_17](doc/img/rapbian-images/17.PNG)

Preguntanos se queremos actualizar o software, preferimos actualizar manualmente máis tarde polo que declinamos:

![raspbian_18](doc/img/rapbian-images/18.PNG)

Rematamos estas pequenas opcións de configuración:

![raspbian_19](doc/img/rapbian-images/19.PNG)

Imos agora á consola e actualizamos:

![raspbian_20](doc/img/rapbian-images/20.PNG)

![raspbian_21](doc/img/rapbian-images/21.PNG)

## SECURIZACIÓN BÁSICA DE RASPBERRY PI OS

Imos executar unhas pequenas medidas de securización para o sistema, ainda que máis tarde implementaremos algunha ferramenta para este propósito, hai que tomar certas precaucións sempre que vaiamos utilizar un sistema con saída a Internet.

Instalaremos o cortafogos UFW, para poder bloquear portos do noso sistema. Ainda que o máis posible é que o noso router xa bloquee as peticións da maioría dos portos e teña só habilitados os necesarios, nunca está de máis estar seguros, ademais de que imos administrar algúns dos portos da máquina:
Para instalar o cortafogos UFW utilizamos o comando:

`# sudo apt install ufw -y`

![raspbian_22](doc/img/rapbian-images/22.PNG)

O seguinte que imos facer é eliminar o usuario por defecto pi. Antes crearemos outro usuario:

`# sudo adduser radmin`

![raspbian_23](doc/img/rapbian-images/23.PNG)



Engadimolo os grupos do sistema, ademais dos grupos de administración **sudo** e **adm**. Comprobamos que está nos grupos:

`# sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi nuevousuario`

![raspbian_24](doc/img/rapbian-images/24.PNG)

Unha vez engadido entramos como o usuario e comprobamos que temos permisos:

![raspbian_25](doc/img/rapbian-images/25.PNG)

Agora, pechamos sesión e iniciamos co noso **radmin** para eliminar o usuario **pi**:

![raspbian_26](doc/img/rapbian-images/26.PNG)

Eliminamos todos os procesos activos que tiveran que ver co usuario **pi** co seguinte comando:

`# sudo pkill -eu pi`

![raspbian_27](doc/img/rapbian-images/27.PNG)

Eliminamos o usuario con:

`# sudo userdel --remove-home pi`

![raspbian_28](doc/img/rapbian-images/28.PNG)

E eliminamos o arquivo do usuario pi do sudoers:

`# sudo rm /etc/sudoers.d/010_pi-nopasswd`

### SECURIZACIÓN DO SERVIZO SSH

Por último, imos securizar a nosa conexión SSH. Xa que o máis normal é que no futuro nos conectemos fora da nosa rede local, debemos prepararnos para que os intrusos non teñan fácil entrar á nosa máquina.

O primeiro paso será cambiar certas cousas no arquivo de configuración** /etc/ssh/sshd_config**:
- Cambiamos o porto do servizo, por exemplo por o 3578.
- Denegamos o inicio de sesión ó usuario root.
- Modificamos a cantidade de tempo que a pantalla de login estará dispoñible a 1 minuto.
- Cambiamos os valores de máximos intentos de inicio a 3 e de máximas sesións abertas de forma simultanea a 2.
- Obligamos a que na autentificación sempre esixa un contrasinal e que non permita contrasinais vacíos.
- Tamén lle indicamos os usuarios permitidos, neste caso o noso **radmin**, e os denegados, que neste caso queremos que sexa o **root**. 



Revisamos a sintaxe do ficheiro despois dos cambios, se non da saída significa que está correcta:

`# sudo sshd -t`

![raspbian_29](doc/img/rapbian-images/29.PNG)

Reiniciamos o servizo co seguinte comando:

`# sudo systemctl restart sshd`

Vemos que os cambios se efectuaron correctamente:

![raspbian_30](doc/img/rapbian-images/30.PNG)