O proxecto vai consistir na creación dun sistema de videovixilancia nunha Raspberry Pi (aínda que podería ser en calquera
máquina con un sistema GNU/Linux dispoñible), escalable e flexible, de software libre para utilizar nun ámbito
doméstico (quizáis no futuro se poderían ampliar as súas capacidades e funcionalidades). Con isto en mente, executaríase a
parte documental de todo o proceso ademais de presentar un sistema funcional na realidade.

Coa situación de pandemia que temos na actualidade, moita xente teme que vaian asaltar ou okupar as súas segundas vivendas ou outras estancias.
Existen xa, moitas empresas que ofrecen unha solución, o problema é que teñen un custo elevado ó inicio. Ademais,
normalmente, hai que pagar unha mensualidade por moitos deses servizos para desfrutar do que anuncian (aviso á policía,
comprobación das imaxes en dispositivos multiplataforma en tempo real...). Moita xente non está disposta ou non ten medios para pagar tal cantidade de diñeiro. Tamén se dispón no mercado dunha alternativa máis económica, sen embargo, require duns coñecementos previos. A posibilidade de comprar un NVR e colocalo un mesmo no seu fogar é moito máis accesible que contratar un terceiro. Igualmente, moitos deses aparellos non ofrecen todas as solucións por se queremos ampliar as súas funcionalidades poden non ser compatibles ou implicaría invertir máis nunha máquina que si sexa compatible con todas as funcións.

Recapitulando un pouco o anteriormente citado, o obxectivo sería unha implementación exitosa dun sistema que poida monitorizar unha ou máis cámaras de varios tipos, que se poidan consultar fóra da rede tanto en PCs coma en dispositivos móbiles. Tamén que se poidan almacenar as imaxes nunha nube privada e recibir alertas por algunha vía cando se detecte movemento, sexa por correo, SMS... Por suposto, debe estar correctamente securizado para que non accedan intrusos ou persoas non autorizadas ó noso sistema ademais de estar dotado dun software de monitorización por se en caso de caídas, tamén se nos notifique. 

Para implementalo, utilizarase unha Raspberry Pi 3 B+, ademais de unha ou varias cámaras IP de marcas variadas que posúo, a cámara de Raspberry, cámaras USB, etc. Todas estas cousas mencionadas serían os mínimos que debe ter para que cumpra a súa función, pero sempre se pode aumentar e súa funcionalidade.

Por outra banda o software a utilizar sería o seguinte:
- Sistema Operativo: Raspbian.
- Software para o sistema de videovixilancia: Motion, MotionEye.
- Sistema de monitorización da rede: Icinga2.
- Sistema de almacenamento na nube: software como NextCloud ou Owncloud.
- Alertas ó usuario por correo, SMS, bot de Telegram...
- Securización de rede: iptables, Fail2ban...

En canto á comercialización do mesmo, a idea é facelo como un proxecto aberto, do que todo o mundo poida sacar o coñecemento e implementalo libremente. O software utilizado posúe licenzas de software libre e a Raspberry Pi, unha vez adquirida tes toda a potestade de facer o que desexes con ela, sen embargo, hai que ter en conta que gran parte do contido do SO Raspbian ten licencia GPL, polo que o único que piden dende a Raspberry Pi Foundation é que se debe proporcionar acceso ó código fonte se é solicitado. Tendo iso en conta, poderíamos ter unha oportunidade de negocio real, ainda que, prefiro que sexa un proxecto libre.
