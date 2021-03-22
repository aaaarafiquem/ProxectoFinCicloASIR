# FASE DE PLANIFICACIÓN DO PROXECTO

## Obxectivos do proxecto

## Guía de planificación do proxecto

### Metodoloxía


### Fases planificadas

Descríbense as fases en que se divide o proxecto e as tarefas que se han levar a cabo en cada unha destas fases.
Pódense indicar os recursos materiais e humanos asociados a cada tarefa ou, se son os mesmos, de maneira máis xeral.

#### Fase 1: Análise do entorno

##### Tarefa 1: Desplazamento ó domicilio ou negocio 

Descrición: Desprazarémonos ó sitio onde se desplegará o sistema para que o cliente nos explique o que necesita e poder ver as instalacións para planificar a implementación. 

Recursos necesarios: un vehículo para desprazarse en caso de ser necesario.

##### Tarefa 2: Análise do marco de traballo

Descrición: Unha vez no lugar, faremos un estudo da estrutura de rede do cliente basándonos nos seus requerimentos.

Recursos necesarios: Un metro e unha libreta para apuntar todo o necesario.

#### Fase 2: Configuración do hardware base

##### Tarefa 1: Instalación e configuración de Raspberry Pi OS

Descrición: Instalarase o Sistema Operativo e farase a configuración básica tal e como se explica no [punto 5.1](doc/documentacion/raspbian.md).

Recursos hardware/software:
- Raspberry Pi 3 B+
- Carcasa para Raspberry Pi
- Kit de ferramentas básicas (desparafusadores, tornillos...)
- Imaxe do Sistema Operativo
- Conexión a Internet

#### Fase 3: Instalación do software para o CCTV: MotionEye

##### Tarefa 1: Instalación de MotionEye

Descrición: Executar a instalación de MotionEye no sistema, seguindo os pasos do [punto 5.2](doc/documentacion/motioneye.md).

Recursos hardware/software:

- Repositorio de MotionEye
- Conexión a Internet

##### Tarefa 2: Configuración previa de cámaras

Descrición: Facer a configuración previa de sincronización de cámaras IP ca rede WiFi ou montar as cámaras no servidor.

Recursos hardware/software:

- Tipo de cámaras desexado
- Apps móbiles para cada cámara dependendo da marca (en caso de necesitala)
- Conexión a Internet

##### Tarefa 3: Engadir e configurar cámaras en MotionEye

Descrición: Configurar as cámaras en MotionEye poñendo onde queremos que se garden as imaxes, o texto en pantalla...

- Instalación de MotionEye completada e funcional

#### Fase 4: Instalación do software de monitorización: Icinga2

##### Tarefa 1: Instalación de Icinga2

Descrición: Levarase a cabo a instalación de Icinga2, seguindo os pasos do [punto 5.3](doc/documentacion/icinga2.md).

Recursos hardware/software:

- Repositorio de Icinga2 e dependencias
- Conexión a Internet

##### Tarefa 2: Adquisición de nome de dominio e certificado SSL

Descrición: Dentro do marco da instalación de Icinga2, creamos un nome de dominio (no noso caso, un gratuito). Indicado tamén no [punto 5.3](doc/documentacion/icinga2.md).

Recursos hardware/software:

- Conta en FreeNom
- Creación do certificado
- Os paquetes de CertBot, SSL e rewrite de Apache2.
- Conexión a Internet

##### Tarefa 3: Instalación de Dashing Dashboard

Descrición: Instalación do Icinga2 Dashing Dashboard. Farase tamén a configuración básica tal e como se explica no [punto 5.4](doc/documentacion/icinga2_dashing_dashboard.md).

Recursos hardware/software:

- Repositorio de Dashing Dashboard e dependencias
- Conexión a Internet

##### Tarefa 4: Apertura de portos no router

Descrición: Abriranse os portos necesarios no router do cliente. Dependendo do operador, poderá variar a maneira de facelo.

**NOTA:** No meu caso, fixen unha pequena guía da apertura dos portos nun router de R (que están moi capados) explicada no [punto 5.5](doc/documentacion/apertura_de_portos.md).

Recursos hardware/software:

- As credenciais de acceso ó router.
- Un ordenador portátil para poder acceder ó router.


#### Fase 5: Configuración de alertas dos servizos

##### Tarefa 1: Configuración de Postfix

Descrición: Configuraremos Postfix para que o noso servidor teña a capacidade de enviar correos por si mesmo.

Recursos hardware/software: 

- Paquetes Postfix e mailutils
- Conta en Gmail ou outro proveedor de correo
- Conexión a Internet

##### Tarefa 2: Alertas de MotionEye

Descrición: Configuraránse as alertas dentro da propia aplicación de MotionEye. Explicado no [punto 5.6](doc/documentacion/motioneye_alertas.md). 

Recursos hardware/software: realmente ningún adicional, só poder acceder a MotionEye e o correo en cuestión.

##### Tarefa 3: Alertas de Icinga2

Descrición: Configuraránse as alertas según as necesidades do cliente, tendo en conta a configuración da tarefa 1 e o explicado no [punto 5.7](doc/documentacion/icinga2_alertas.md).

Recursos hardware/software: 

- Documentacion necesaria, dispoñible na [páxina oficial de Icinga2](https://icinga.com/docs/icinga-2/latest/doc/03-monitoring-basics/#notifications)
- Conexión a Internet

#### Fase 6: Comprobación do correcto funcionamento dos servizos

##### Tarefa 1: Comprobamos que chegamos ós nomes de dominio 

Descrición: Comprobamos que chegamos correctamente cos nomes do noso dominio e as redireccións.

### Diagrama de Gantt
Un diagrama de Gantt é unha representación gráfica da secuenciación que tes que seguir para realizar as tarefas planificadas. Pódese usar o software "Gantt project" ou calquera outro que permita representar nun cronograma a información relativa á planificación de tarefas. 

## Orzamento

| CONCEPTO | IMPORTE|
|--|--|
| Raspberry Pi 3 B+ | 36,95 € 
| Tarxeta MicroSD | 7,71 €
| Carcasa para Raspberry Pi | 10,99 €
| Raspberry Cámara V2 | 29,99 €
| Xiaomi MI Home Security Camera 360° | 35,97 €
| TP-Link - Cámara IP WiFi 360º | 27,90 €

| TOTAL | PROXECTO | 
|--|--|
| -- | 149,51 € |

### WEBGRAFÍA
Guía para a elaboración de proyectos. Gobierno Vasco.
https://www.pluralismoyconvivencia.es/upload/19/71/guia_elaboracion_proyectos_c.pdf  (páxina 49 e seguintes)



