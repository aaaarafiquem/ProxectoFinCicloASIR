#	INSTALACIÓN Icinga2

Neste punto do proxecto abordamos a instalación da aplicación de monitorización da rede, moi necesaria nestes tempos nos que necesitamos saber se un servidor ou un servizo se viu comprometido ou sufriu unha caída. No noso caso escollín Icinga2, un software de monitorización de código aberto. É un fork do coñecido Nagios no ano 2009. A versión máis recente é a 2.11.8 (decembro de 2020). Icinga2 ademais, conta con unha gran varidade de módulos e plugins creados pola comunidade que axudan a todo o mundo. Para instalar o servizo na nosa máquina, seguimos os seguintes pasos:

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

Instalamos ahora el servidor web de Apache:

`# apt install apache2 -y`

Añadimos la regla para el puerto 80 en el firewall e instalamos iptables-persistent para que la guarde:

`# iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT`

`# apt install iptables-persistent`

Preparamos la API de Icinga2:

`# icinga2 api setup`

En el fichero /etc/icinga2/conf.d/api-users.conf la información del usuario:

`object ApiUser "icingaweb2" {
  password = "abc123."
  permissions = [ "status/query", "actions/*", "objects/modify/*", "objects/query/*" ]
}`

Reiniciamos el servicio:

`# systemctl restart icinga2`

Instalamos Icinga Web 2:

`# apt-get install icingaweb2 icingacli -y`

Nos aseguramos de que el grupo de icingaweb2 exista y además como grupo www-data:

`# addgroup --system icingaweb2`

`# usermod -a -G icingaweb2 www-data`

También cambiamos el directorio de configuración:

`# icingacli setup config directory --group icingaweb2`

Ahora creamos el token de instalación con el siguiente comando:

`# icingacli setup token create`

Pasamos agora, á configuración na interface web. Para iso imos ó noso navegador favorito e poñemos "**IPServidor/icingaweb2/setup**"








