#	INSTALACIÓN Icinga2

## Credenciais de acceso a Icinga Web 2

Para acceder imos á páxina dedicada no proxecto de [Icinga Web 2](https://raspbicctv.ga/icingaweb2/).

**Usuario administrador**
- **Nome usuario:** icinga2admin
- **Contrasinal:** t&Y(:dGM4Ds+VxfL

## Instalación

Aseguramonos que a máquina está actualizada:

`$ sudo apt update && apt upgrade -y`

Instalamos as ferramentas necesarias:

`$ sudo apt-get -y install apt-transport-https wget gnupg`

Engadimos os repositorios de Icinga2 cos seguintes comandos:

`$ sudo wget -O - https://packages.icinga.com/icinga.key | apt-key add -`

![icinga2_1](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/1.PNG)

Engadimos o repositorio o da seguinte orde:

`DIST=$(awk -F"[)(]+" '/VERSION=/ {print $2}' /etc/os-release); \
 echo "deb https://packages.icinga.com/debian icinga-${DIST} main" > \
 /etc/apt/sources.list.d/${DIST}-icinga.list
 echo "deb-src https://packages.icinga.com/debian icinga-${DIST} main" >> \
 /etc/apt/sources.list.d/${DIST}-icinga.list`

![icinga2_2](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/2.PNG)

Actualizamos para que se engadan os paquetes:

`$ sudo apt-get update`

![icinga2_3](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/3.PNG)

Instalamos Icinga2:

`$ sudo apt-get install icinga2 -y`

![icinga2_4](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/4.PNG)

Instalamos os check plugins de Icinga2:

`$ sudo apt-get install monitoring-plugins -y`

![icinga2_6](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/6.PNG)

Faranos a seguinte pregunta, que dependendo da nosa configuración respoderemos **Sí** ou **No**:

![icinga2_7](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/7.PNG)

Comprobamos no directorio por defecto **/var/lib/nagios/plugins/** que, efectivamente, alí se atopan:

![icinga2_5](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/5.PNG)

Habilitamos o servizo de Icinga2:

`$ sudo systemctl enable icinga2`

![icinga2_9](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/9.PNG)

Revisamos o estado do servizo de Icinga2:

`$ sudo systemctl status icinga2`

![icinga2_8](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/8.PNG)

Instalamos o paquete de sintaxis de vim, o que nos vai permitir desfrutar de detección de tipo de arquivo e resaltado de sintaxis para os arquivos de configuración de Icinga 2:

`$ sudo apt-get install vim-icinga2 vim-addon-manager -y`

Activamolo para Icinga2:

`$ sudo vim-addon-manager -w install icinga2 `

Instalamos o servidor de base de datos, neste caso, MariaDB:

`$ sudo apt install mariadb-server mariadb-client -y`

![icinga2_10](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/10.PNG)

`$ sudo mysql_secure_installation`

Instalamos o módulo IDO MySQL de Icinga, respondendo a unha serie de cuestións:

`$ sudo apt-get install icinga2-ido-mysql`

![icinga2_11](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/11.PNG)

Responderemos as seguintes preguntas dependendo da configuración desexada:

![icinga2_12](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/12.PNG)

![icinga2_13](doc/img/icinga2_images/13.PNG)

Poñemos o contrasinal para a aplicación:

![icinga2_14](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/14.PNG)

![icinga2_15](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/15.PNG)

Creamos a base de datos para Icinga:

`$ sudo mysql -u root -p`

`> CREATE DATABASE icinga2;`

`> GRANT SELECT, INSERT, UPDATE, DELETE, DROP, CREATE VIEW, INDEX, EXECUTE ON icinga2.* TO 'icinga2'@'localhost' IDENTIFIED BY 'password';`

![icinga2_16](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/16.PNG)

Importamos o esquema IDO de Icinga 2 usando o seguinte comando:

`# mysql -u root -p icinga < /usr/share/icinga2-ido-mysql/schema/mysql.sql`

![icinga2_17](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/17.PNG)

Habilitamos o módulo **ido-mysql**:

`$ sudo icinga2 feature enable ido-mysql`

![icinga2_18](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/18.PNG)

Reiniciamos o servizo:

`$ sudo systemctl restart icinga2`

`$ sudo icinga2 daemon -C`

![icinga2_19](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/19.PNG)

Instalamos ahora o servidor web de Apache:

`$ sudo apt install apache2 -y`

![icinga2_20](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/20.PNG)

Instalamos IcingaWeb2 e as dependencias necesarias:

`$ sudo apt install icingaweb2 icingacli libapache2-mod-php php-gd -y`

![icinga2_21](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/21.PNG)

Activamos os portos no firewall para o servizo web:

![icinga2_49](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/49.PNG)


## Activación do SSL e certificado de Let's Encrypt - Parte 1

Habilitamos o módulo SSL e rewrite de Apache2:

![icinga2_22](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/22.PNG)

Instalamos Certbot para posteriormente crear un certificado para o noso Host:

![icinga2_23](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/23.PNG)

###  Creación de nome de dominio en FreeNom

Antes de seguir, facer un pequeno inciso para ir á [páxina de FreeNom](https://my.freenom.com/) e crear unha conta.

Unha vez feito, poderemos comprobar a dispoñibilidade do nome que desexemos:

![icinga2_46](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/46.PNG)


A continuación, se está dispoñible poderemos elixir algún dos 5 dominios xeográficos gratuitos dispoñibles que son de pequenos países do mundo.

![icinga2_47](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/47.PNG)
**(Como esta captura foi feita despois de facer o dominio deste proxecto, o .ga, se alguén o quere reclamar terá que pagar unha cantidade de cartos como aqí se mostra).**


Para exemplificalo, imos coller o .tk para ver que, efectivamente, nos da a opción de ata un ano gratuito para o uso deste nome de dominio:

![icinga2_48](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/48.png)

Finalmente, podemos administrar o noso dominio dende a nosa conta:

![icinga2_44](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/44.PNG)

Aquí poñemos a IP pública do noso router para redireccione o tráfico aí:

![icinga2_45](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/45.png)

## Activación do SSL e certificado de Let's Encrypt - Parte 2

Unha vez feito o anterior, executamos o comando 

![icinga2_25](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/25.PNG)

Podemos executar análise do certificado do noso dominio [neste link](https://www.ssllabs.com/ssltest/analyze.html?d=raspbicctv.ga) que nos devolverá  un informe do mesmo.

## Preparación de IcingaWeb2

Preparamos a API de Icinga2:

`$ sudo icinga2 api setup`

**(Esta é unha captura despois de haber executado o comando unha vez)**
![icinga2_50](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/50.PNG)

No fichero /etc/icinga2/conf.d/api-users.conf a información do usuario:

`object ApiUser "icingaweb2" {
  password = "abc123."
  permissions = [ "status/query", "actions/*", "objects/modify/*", "objects/query/*" ]
}`
 

(Sustituiremos abc123. por un **contrasinal robusto**).

![icinga2_51](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/51.PNG)

Cambiamos a zona horaria no ficheiro **/etc/php/7.3/apache2/php.ini**:

![icinga2_24](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/24.PNG)

Reiniciamos o servicio:

`$ sudo systemctl restart icinga2`

E tamén o servizo web.

`$ sudo systemctl restart apache2`

Aseguramonos de que o grupo de **icingaweb2** exista e ademais tamén o grupo **www-data**:

`$ sudo addgroup --system icingaweb2`

`$ sudo usermod -a -G icingaweb2 www-data`

Tamén cambiamos o directorio de configuración:

`$ sudo icingacli setup config directory --group icingaweb2`

Agora creamos o token de instalación co seguinte comando:

`$ sudo icingacli setup token create`


## Instalación na interface web

Pasamos agora, á configuración na interface web. Para iso imos ó noso navegador favorito e poñemos "**IPServidor/icingaweb2/setup**".

Introducimos o token que nos deron os comandos anteriores:

![icinga2_26](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/26.PNG)

Escollemos os módulos a instalar, neste caso o de monitorización de forma obligatoria, tamén podemos escoller, por exemplo, o módulo de documentación para tela máis a man:

![icinga2_27](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/27.PNG)

Comprobamos que temos todos os módulos necesarios:

![icinga2_28](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/28.PNG)

Escollemos o método de autentificación:

![icinga2_29](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/29.PNG)

Poñemos agora, os datos a base de datos para IcingaWeb2:

![icinga2_31](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/31.PNG)


Escollemos o método de autentificación do backend:

![icinga2_32](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/32.PNG)

Creamos a conta de administrador para IcingaWeb2:

![icinga2_33](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/33.PNG)

Configuramos todo o que ten que ver a nivel aplicación e logging:

![icinga2_34](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/34.PNG)

Vemos un pequeno resumo da configuración de IcingaWeb2:

![icinga2_35](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/35.PNG)

Comezamos agora, ca configuración do módulo de monitorización de IcingaWeb2:

![icinga2_36](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/36.PNG)

Configuramos como IcingaWeb2 recuperará a información de monitorización:

![icinga2_37](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/37.PNG)

Cubrimos cos datos da base de datos do módulo IDO-MySQL:

![icinga2_38](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/38.PNG)

Definimos como vai enviar os comandos á instancia de monitorización, definese que se enviarán a través da API de Icinga2 co usuario que creamos anteriormente no ficheiro **/etc/icinga2/conf.d/api-users.conf**.

![icinga2_39](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/39.PNG)

Deixamos as variables de protección por defecto para que oculte os contrasinais:

![icinga2_40](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/40.PNG)

Vemos un resumo da configuración asignada ó módulo de monitorización antes de rematar:

![icinga2_41](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/41.PNG)

Instalouse de forma satisfactoria:

![icinga2_42](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/42.PNG)

Iniciamos sesión co usuario de administración que creamos durante a instalación:

![icinga2_52](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/52.PNG)

Vemos como está monitorizando o noso propio servidor, e funciona de forma correcta.

Como monitoriza o servizo ssh polo porto 22, da fallo xa que o servizo está correndo por outro porto. Este problema solucionarase máis adiante:

![icinga2_43](https://github.com/aaaarafiquem/ProxectoFinCicloASIR/blob/master/doc/img/icinga2_images/43.PNG)







