#	INSTALACIÓN Icinga2

Aseguramonos que a máquina está actualizada:

`# apt update && apt upgrade -y`

Instalamos as ferramentas necesarias:

` # apt-get -y install apt-transport-https wget gnupg`

Engadimos os repositorios de Icinga2 cos seguintes comandos:

`# wget -O - https://packages.icinga.com/icinga.key | apt-key add -`

Engadimos o repositorio o da seguinte orde:

`DIST=$(awk -F"[)(]+" '/VERSION=/ {print $2}' /etc/os-release); \
 echo "deb https://packages.icinga.com/debian icinga-${DIST} main" > \
 /etc/apt/sources.list.d/${DIST}-icinga.list
 echo "deb-src https://packages.icinga.com/debian icinga-${DIST} main" >> \
 /etc/apt/sources.list.d/${DIST}-icinga.list`

Actualizamos para que se engadan os paquetes:

`# apt-get update`

Instalamos Icinga2:

`# apt-get install icinga2 -y`

Instalamos os check plugins de Icinga2:

`# apt-get install monitoring-plugins -y`

Habilitamos o servizo de Icinga2:
`# systemctl enable icinga2`

Instalamos o paquete de sintaxis de vim, o que nos vai permitir desfrutar de detección de tipo de arquivo e resaltado de sintaxis para os arquivos de configuración de Icinga 2:

`# apt-get install vim-icinga2 vim-addon-manager -y`

Activamolo para Icinga2:

`# vim-addon-manager -w install icinga2 `

Instalamos o servidor de base de datos, neste caso, MariaDB:

`# apt install mariadb-server mariadb-client -y`

`# mysql_secure_installation`

Instalamos o módulo IDO MySQL de Icinga, respondendo a unha serie de cuestións:

`# apt-get install icinga2-ido-mysql`

Creamos a base de datos para Icinga:

`# mysql -u root -p`

`> CREATE DATABASE icinga2;`

`> GRANT SELECT, INSERT, UPDATE, DELETE, DROP, CREATE VIEW, INDEX, EXECUTE ON icinga2.* TO 'icinga2'@'localhost' IDENTIFIED BY 'password';`

Habilitamos o módulo ido-mysql:

`# icinga2 feature enable ido-mysql`

Reiniciamos o servizo:

`# systemctl restart icinga2`

Instalamos ahora o servidor web de Apache:

`# apt install apache2 -y`

Engadimos a regra para o puerto 80 no firewall e instalamos iptables-persistent para que a guarde:

`# iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT`

`# apt install iptables-persistent`

Preparamos a API de Icinga2:

`# icinga2 api setup`

No fichero /etc/icinga2/conf.d/api-users.conf a información do usuario:

`object ApiUser "icingaweb2" {
  password = "abc123."
  permissions = [ "status/query", "actions/*", "objects/modify/*", "objects/query/*" ]
}`

Reiniciamos o servicio:

`# systemctl restart icinga2`

Instalamos IcingaWeb2:

`# apt-get install icingaweb2 icingacli -y`

Aseguramonos de que o grupo de **icingaweb2** exista e ademais tamén o grupo **www-data**:

`# addgroup --system icingaweb2`

`# usermod -a -G icingaweb2 www-data`

Tamén cambiamos o directorio de configuración:

`# icingacli setup config directory --group icingaweb2`

Agora creamos o token de instalación co seguinte comando:

`# icingacli setup token create`

Pasamos agora, á configuración na interface web. Para iso imos ó noso navegador favorito e poñemos "**IPServidor/icingaweb2/setup**"

![icinga2_14](doc/img/icinga2_images/14.PNG)


Imos asegurarnos de que temos o grupo **icingaweb2** e que o usuario pertence tamén ó grupo **www-data**, cambiamos o directorio de configuración.
Finalmente, imos crear o token de instalación que nos require a aplicación web para continuar:

![icinga2_13](doc/img/icinga2_images/13.PNG)

Escollemos os módulos a instalar, neste caso o de monitorización de forma obligatoria, tamén escollín o módulo de documentación para tela máis a man:

![icinga2_15](doc/img/icinga2_images/15.PNG)

Comprobamos que temos todos os módulos necesarios:

![icinga2_16](doc/img/icinga2_images/16.PNG)

Escollemos o método de autentificación:

![icinga2_17](doc/img/icinga2_images/17.PNG)

Creamos agora, a base de datos para IcingaWeb2. Para isto, volvemos a nosa máquina e poñemos no noso servidor de base de datos o seguinte:

![icinga2_18](doc/img/icinga2_images/18.PNG)

Poñemos agora, os datos da base que acabamos de crear:

![icinga2_19](doc/img/icinga2_images/19.PNG)

Escollemos o método de autentificación do backend:

![icinga2_20](doc/img/icinga2_images/20.PNG)

Creamos a conta de administrador para IcingaWeb2:

![icinga2_21](doc/img/icinga2_images/21.PNG)

Configuramos todo o que ten que ver a nivel aplicación e logging:

![icinga2_22](doc/img/icinga2_images/22.PNG)

Vemos un pequeno resumo da configuración de IcingaWeb2:

![icinga2_23](doc/img/icinga2_images/23.PNG)

Comezamos agora, ca configuración do módulo de monitorización de IcingaWeb2:

![icinga2_24](doc/img/icinga2_images/24.PNG)

Configuramos como IcingaWeb2 recuperará a información de monitorización:

![icinga2_25](doc/img/icinga2_images/25.PNG)

Cubrimos cos datos da base de datos do módulo IDO-MySQL:

![icinga2_26](doc/img/icinga2_images/26.PNG)

Definimos como vai enviar os comandos á instancia de monitorización, definese que se enviarán a través da API de Icinga2 co usuario que creamos anteriormente no ficheiro **/etc/icinga2/conf.d/api-users.conf**.

![icinga2_27](doc/img/icinga2_images/27.PNG)

Deixamos as variables de protección por defecto para que oculte os contrasinais:

![icinga2_28](doc/img/icinga2_images/28.PNG)

Vemos un resumo da configuración asignada ó módulo de monitorización antes de rematar:

![icinga2_29](doc/img/icinga2_images/29.PNG)

Instalouse de forma satisfactoria:

![icinga2_30](doc/img/icinga2_images/30.PNG)

Iniciamos sesión co usuario de administración que creamos durante a instalación:

![icinga2_31](doc/img/icinga2_images/31.PNG)

Vemos cómo está monitorizando o noso propio servidor, e funciona de forma correcta:

![icinga2_32](doc/img/icinga2_images/32.PNG)







