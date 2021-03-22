# INSTALACIÓN e CONFIGURACIÓN de Dashing Dashboard en Icinga2

## Acceso a Icinga2 Dashing Dashboard

Para acceder imos á páxina dedicada no proxecto do [Icinga2 Dashing Dashboard](https://raspbicctv.ga/icinga2).


## Instalación

Para instalar o Dashing Dashboard para Icinga2, só temos que seguir as instruccións do [repositorio oficial](https://github.com/mocdaniel/dashing-icinga2).

Primeiro que nada, situarnos no directorio **/usr/share/**:

`$ cd /usr/share`

E descargamos o contido do repositoiro mediante wget:

`$ sudo wget https://github.com/mocdaniel/dashing-icinga2/archive/master.zip`

![icinga2_dashing_dashboard_1](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/1.PNG)

Descomprimimos o contido co comando unzip:

`$ sudo unzip master.zip`

![icinga2_dashing_dashboard_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/2.PNG)

Cambiamos o nome do directorio e accedemos a él:

`mv dashing-icinga2-master dashing-icinga2`

`$ sudo cd dashing-icinga2`

Instalamos os paquetes ruby bundler nodejs:

`$ sudo apt-get -y install ruby bundler nodejs`

![icinga2_dashing_dashboard_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/3.PNG)

Creamos un usuario novo para o servizo dashing, xa que **non se debe executar como root**.

![icinga2_dashing_dashboard_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/5.PNG)

![icinga2_dashing_dashboard_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/4.PNG)

Proceda coa instalación da gem con bundler:

![icinga2_dashing_dashboard_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/6.PNG)

Instalamos as dependencias necesarias con bundler, pero co usuario dashing:

![icinga2_dashing_dashboard_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/7.PNG)

Creamos un usuario na REST API de Icinga2 para o Dashboard (substituímos o contrasinal _abc123._ por un máis robusto):

![icinga2_dashing_dashboard_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/8.PNG)

Configuramos o arquivo **/usr/share/dashing-icinga2/config/icinga2.local.json** cubrindoo según as nosas necesidades:

![icinga2_dashing_dashboard_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/9.PNG)

Abrimos o porto 8005 no _firewall_, o que utiliza este servizo:

![icinga2_dashing_dashboard_12](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/12.PNG)

Instalamos o ficheiro Systemd proporcionado desde **/usr/share/dashing-icinga2/tools/systemd**:

![icinga2_dashing_dashboard_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/10.PNG)

Finalmente, temos aquí o Dashboard:

![icinga2_dashing_dashboard_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_dashing_dashboard/11.PNG)
