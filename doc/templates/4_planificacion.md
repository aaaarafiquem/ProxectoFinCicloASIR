# FASE DE PLANIFICACIÓN DO PROXECTO

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

Neste punto teremos a imaxe do que se tardou en investigar e executar as tarefas referentes á creación deste proxecto.

![diagrama_gantt](doc/img/diagramas_images/diagrama_gantt.png)

**Feito con Gantt Project**

## Orzamento

A seguinte táboa mostra o orzamento real que se levou a cabo para executar este proxecto na realidade. O importe dos artigos é orientativo xa que, o prezo pode variar dependendo do paso do tempo ou da dispoñibilidade de ofertas.

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

## Orzamento no suposto da creación dunha empresa

### Trámites necesarios

Como se falou en anteriores puntos, no suposto de crear unha empresa, estimouse que a creación dunha Sociedade Limitada sería o adecuado.

Para crear unha **sociedade limitada (S.L.)** teremos que ter claros os trámites obrigatorios:

1. **Rexistrar o nome da empresa**

Deberíamos dirixirnos ó Rexistro Mercantil Central e solicitar o certificado negativo de denominación social, é dicir, o documento que acredita que o nome elixido para a sociedade ou empresa non coincide co de ningunha outra sociedade xa existente. 
Para a obtención deste certificado debemos presentar o documento no que figuren tres posibles nomes para a empresa. Este trámite pódese realizar online na web do Rexistro Mercantil (o que sería perfecto tendo en conta os tempos que corren) central dende 16 euros. 
Unha vez concedido o certificado, o nome quedará reservado durante seis meses. En caso de superar este período, debemos proceder a renovación do mesmo. 

2. **Abrir unha conta bancaria a nome da empresa**

Unha vez obtido o certificado, debemos de abrir unha conta bancaria a nome da empresa que se vai constituir e ingresar o capital mínimo inicial, uns 3.000 euros de forma íntegra. O banco emitirá un certificado de dito ingreso que posteriormente se presentará na notaría. 

Normalmente non nos permitirán dispor dos cartos ata que presentemos no banco a alta en Facenda e as escrituras selladas polo rexistro mercantil.

3. **Redacción dos Estatutos Sociales**

Os socios deberán redactar os Estatutos Sociaies, que son o conxunto de normas que rexirán a empresa e que se incorporarán posteriormente á escritura pública da constitución. Normalmente, esta tarefa delegase a un abogado ou notaría pola complexidade da mesma, aínda que, agora este trámite simplificouse moito se se crea a SL a través dun PAE, xa que se usan uns estatutos simplificados tipo sen custo.

Existen unha serie de elementos mínimos cos que debe contar calquera Estatuto Social, tales como a **denominación da sociedade**, na que deberá figurar necesariamente a expresión **“sociedade de responsabilidade limitada”**; o **Obxecto social ou actividade** á que se vai adicar a sociedade, **a data de peche de cada exercicio**, o d**omicilio social** dentro do territorio español, **o capital social**, as **participacións** en que se divida, **valor nominal** de cada participación e numeración das mesmas, e o sistema de **administración da sociedade**.

4. **Escritura pública da constitución**

A firma da escritura pública da constitución da sociedade por parte de todos os socios realízase ante notario, o que conleva un pequeno custo, xeralmente un porcentaxe sobre o capital escriturado. É un trámite previo á posterior inscripción no Rexistro Mercantil. Para isto é necesario aportar a seguinte documentación:
	-   Estatutos Sociales da Sociedade.
    - 	O orixnal da Certificación negativa do registro mercantil central.
    - 	Certificación bancaria da aportación diñeiral do Capital Social.
    - 	D.N.I. orixinal de cada un dos socios fundadores.
    - 	Declaración de inversións exteriores (en caso de que algún dos socios sexa estranxeiro).

5. Liquidación do Impuoto sobre Transmisións Patrimoniais
O Impuesto sobre Transmisións Patrimoniais e Actos Xurídicos Documentados é un tributo que gravaba a constitución da sociedade e que había que liquidar nas oficinas de Facenda da CA nun plazo de 30 días dende o otorgamento da escritura. Para iso, debemos aportar debidamente cumplimentado o **modelo 600**, xunto coa copia simple da escritura pública ou fotocopia da mesma. O seu importe ascendía o 1% do capital social.

6. **Trámites en Facenda**

    6.1. **Obtención do Número de Identificación Fiscal**

    Tras a firma das escrituras, debemos dirixirnos a Facenda para obter o N.I.F. provisional da túa sociedade, que ten unha validez de 6 meses, así como as         etiquetas e tarxetas identificativas. Para isto, debemos aportar debidamente cumprimentado o **modelo 036**, a fotocopia do D.N.I do firmante e     a fotocopia da escritura de constitución da empresa obtida no notario.

    6.2. **Alta no I.A.E.**

    Tamén terás que debemos darnos de alta no Impuesto de Actividades Económicas (IAE). Trátase dun tributo local que grava a actividade de empresas,    profesionais e artistas e necesita de tantas altas como actividades se vaian a desenrolar. Para levar a cabo os trámites de alta, modificación ou baixa deste tributo, será necesario que aportes o modelo 840 xunto co NIF na Administración Tributaria correspondente a onde se exerce a actividade. 
Para os supostos exentos deste gravamen, é dicir, aqueles que teñan unha cifra de negocio inferior a 1.000.000 de euros o ano, só é necesario aportar o modelo 036 da declaración censal indicando os epígrafes IAE aos que te acolles.

    6.3. **Declaración censal (IVA)**

    Nesta declaración detállase o comezo, a modificación ou o cese da actividade. Debe ser presentada por todos os nomeados no punto anterior ademais de todos aqueles con obrigacións tributarias. Para a súa expedición, é necesario aportar o **modelo oficial 036**, o **NIF da Sociedade** e o **documento acreditativo de alta** no **Impuesto de Actividades Económicas**.

7. **Inscripción no Rexistro Mercantil**
A sociedade ten que inscribirse no Rexistro Mercantil da provincia na que se fixou o seu domicilio social. Para isto, ten un plazo de dous meses dende a obtención da escritura da constitución e necesita aportar a seguinte documentación:
    - 	Copia auténtica da escritura de constitución da Sociedade.
    - 	Certificación negativa de denominación social.
    - 	Documento acreditativo de haber liquidado o Impuesto sobre Transmisións Patrimoniais e Actos Xurídicos Documentados.
    - 	Copia do N.I.F. Provisional.
    - 	Este paso tamén se inclúe no DUE, polo que non é necesario acudir o Rexistro Mercantil se traballamos cun PAE como Infoautónomos.


8. **Obtención do N.I.F. definitivo**
    Unha vez completados os pasos anteriores, debemos dirixirnos novamente a Facenda para canxear a tarxeta provisional de N.I.F. pola definitiva, inscribindo efectivamente a constitución da sociedad. Se se fai con DUE poderemos obter o documento de forma telemática.

### Orzamento de taxas dunha empresa

| TAXA | IMPORTE |
|--|--|
| Certificado negativo de denominación social | 16,00 ~ € 
| Capital mínimo inicial | 3.000 €
| Autorización e inscripción de empresas de seguridade | 375,45 €
| Modificación na sede de rexistro do domicilio social, ámbito territorial de actuación e ampliación de actividades, incluído o desprazamento e informe pertinente por parte do persoal da Administración | 263,81 €
| Modificación na sede de rexistro do capital social, propiedade de accións ou participacións, cancelación do rexistro, modificacións estatutarias, variacións na composición persoal dos seus órganos de administración e xestión e na uniformidade do persoal de seguridade | 113,59 €
| Autorización de apertura de delegacións de empresas de seguridade | 142,49 €
| Autorización para abrir un establecemento obrigado a ter medidas de seguridade, exención e exención de medidas de seguridade e, en xeral, outras autorizacións que impliquen desprazamentos e informe do persoal da Administración | 211,84 €
| Habilitación de xestores e xefes de seguridade | 96,27 €
| Habilitación de garda de seguridade e garda rural, incluídas as súas respectivas especialidades | 63,52 €
| Participación nos exames e probas previas á cualificación de gardas de seguridade e gardas rurais, incluídas as súas respectivas especialidades | 23,11 €
| Compulsa de documentos | 3,88 €
| Incremento por cada páxina do documento a compulsar | 1,93 €
| Expedición de certificacións | 23,11 €
| Aumentar por cada páxina de extensión que precise certificación | 1,93 €


| TOTAL | PROXECTO | 
|--|--|
| -- | 4.336,93 € |


### WEBGRAFÍA
Guía para a elaboración de proyectos. Gobierno Vasco.
https://www.pluralismoyconvivencia.es/upload/19/71/guia_elaboracion_proyectos_c.pdf  (páxina 49 e seguintes)



