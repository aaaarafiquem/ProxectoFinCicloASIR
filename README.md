# Sistema de videovixilancia con Raspberry Pi

## Descripción

O proxecto consiste nunha alternativa para implantar nun sistema Linux que fose moito máis configurable que un NVR estándar para ter a nosa vivenda vixiada cando non estamos. A idea sería facer unha infraestructura totalmente configurable e o máis accesible posible para establecer nun ámbito doméstico, o hardware elixido é unha Raspberry Pi, que é compacta, asequible e moi versátil para a nosa tarefa. Podemos utilizar todo tipo de cámaras, ben sexan: cámaras USB, cámaras oficiales de Raspberry, cámaras IP, etc.
Podería contemplarse a posibilidade de engadir tamén sensores de movemento independentes e algunha pequena alarma.
Ademáis, contaría cun sistema de alertas que chegaría a algún medio que o usuario posúa, ben sexa a través de SMS, un bot de Telegram, correo electrónico ou outro medio. Debemos contar con un sistema para almacenar as imaxes no caso de que se detecte movemento, contando ca nosa propia nube privada no propio dispositivo. 
Todos estes servizos deben estar correctamente monitorizados no caso de que fallen, polo que tamén se desplegará un sistema de monitorización de servizos en rede, amais de securizar a rede o mellor posible para que non entren intrusos. 


## Uso

> *TODO*: Es este apartado describe brevemente cómo se usará el software que proyectas. Si tiene una interfaz de terminal, describe aquí su sintaxis. Si tiene una interfaz gráfica de usuario, describe aquí **sólo el uso** (a modo de sumario) **de los aspectos más relevantes de su funcionamiento** (máxima brevedad, como si fuese un anuncio reclamo o comercial).
> Si tu proyecto es documental, realiza una especificación de cómo planteas estas interfaces, con ejemplos incluso o esquemas de diseño. En otras palabras, realiza este apartado independientemente que no haya implementación.

## Sobre el autor

Chámome Rebeca Ledo Barreiro, son Técnico en Sistemas Microinformáticos e Redes (SMR), neste intre estudo Administración de Sistemas Informáticos en Rede do cal, estou a facer as FCT e este mesmo proxecto. De maneira simultánea tamén estudo Desenrolo de Aplicacións Web. 

Este proxecto é unha oportunidade para aprender moito e aproveitar todas as ferramentas e software libre das que dispoñemos na rede.

Sempre fun unha persoa moi curiosa por o mundo da informática, polo que, no meu tempo libre, intento buscar cousas cas que experimentar e das que aprender, tamén por iso, me matriculei en DAW, xa que a programación abre moitas portas para crear moitas cousas de proveito.

## Licencia

Autorizase a copia, distribución e modificación deste documento baixo os termos da licenza de documentación libre GNU, versión 1.3 ou calquera outra que posteriormente publique a Fundación do Software Libre (Free Software Fundation); sen seccións invariantes (Unvariant Sections), textos de portada (Front-Cover Texts), nin textos de contraportada (Back-Cover Texts).



## Índice

1. Anteproyecto
    * 1.1. [Idea](doc/templates/1_idea.md)
    * 1.2. [Necesidades](doc/templates/2_necesidades.md)
2. [Análisis](doc/templates/3_analise.md)
3. [Planificación](doc/templates/4_planificacion.md)
4. [Diseño](doc/templates/5_deseño.md)
5. [Implantación](doc/templates/6_implantacion.md)


## Guía de contribución

As ferramentas e software utilizado neste proxecto son na súa maioría software libre e de código aberto. A mellor forma de contribuír é mellorando calquera destas ferramentas ademáis de contribuír con melloras, novas funcionalidades e ideas para a optimización do conxunto do sistema. 

Por exemplo, podería intentar crease un frontend propio en lugar de utilizar un dunha terceira persoa, entre outras moitas cousas.


## Links

#### Raspberry Pi
- [Páxina de FAQs de Raspberry Pi](https://www.raspberrypi.org/documentation/faqs/#commercial-integrate)
#### Estadísticas e leis
- [Portal Estadístico de Criminalidade (SEC)](https://estadisticasdecriminalidad.ses.mir.es/publico/portalestadistico/portal/balances.html)
- [Documento consolidado BOE-A-2014-3649](https://www.boe.es/buscar/act.php?id=BOE-A-2014-3649&p=20140405&tn=1)
- [Documento consolidado BOE-A-2018-16673](https://www.boe.es/boe_gallego/dias/2018/12/06/pdfs/BOE-A-2018-16673-G.pdf)
- [Guía sobre el uso de videocámaras para seguridad y otras finalidades](https://www.aepd.es/sites/default/files/2019-09/guia-videovigilancia.pdf)
- [Clasificación Nacional de Actividades Económicas](https://www.cnae.com.es/index.php)
#### Documentación
- [Documentación oficial de Motion](https://motion-project.github.io/motion_guide.html)
- [Documentación oficial de MotionEye](https://github.com/ccrisan/motioneye/wiki)
- [Documentación oficial Icinga2](https://icinga.com/docs/icinga-2/latest/doc/01-about/)
- [Documentación oficial Icinga2 Web](https://icinga.com/docs/icinga-web-2/latest/)

#### Licenzas
- [Páxina oficial da Licenza de documentación Libre de GNU](https://www.gnu.org/licenses/fdl-1.3-faq.en.html#top)
- [Traducción non oficial da Licenza de documentación Libre de GNU (Traducida por Víctor Manuel Huezo Lopez)](https://fdl-es.gitlab.io)

#### Varios
- [Regra dos 3 clics](https://es.wikipedia.org/wiki/Regla_de_los_tres_clics)
