### REALIZAR UNA AUDITORÍA DE SEGURIDAD

<p>Se realiza una auditoria del programa de ciberseguridad de la empresa (ficticia) Juguetes ABC con el propósito de alinear las políticas de la empresa con las prácticas estándares de la industria. El objetivo es proporcionar recomendaciones de mitigación para las vulnerabilidades encontradas que sean clasificadas como de alto riesgo y presentar una estrategia general para mejorar la postura de seguridad de la organización.
</p>

#### La auditoría interna de Juguetes ABC analizará lo siguiente:


- Permisos de usuarios actuales creados en: contabilidad, detección de puntos de conexión, cortafuegos (firewalls), sistemas de detección de intrusiones, herramienta de gestión de eventos e información de seguridad (SIEM).
- Controles actuales implementados en: contabilidad, detección de puntos de conexión, cortafuegos (firewalls), sistema de detección de intrusiones, herramienta de gestión de eventos e información de seguridad (SIEM).
- Procedimientos y protocolos actuales establecidos para: contabilidad, detección de puntos de conexión, cortafuegos (firewall), sistema de detección de intrusiones, herramienta de gestión de eventos e información de seguridad (SIEM).
- Comprobar si los permisos, controles, procedimientos y protocolos actuales de los usuarios están alineados con los requisitos de cumplimiento normativo necesarios.
- Verifica si la tecnología actual está debidamente registrada, tanto el hardware como el acceso al sistema.

#### Los objetivos de la auditoría interna de Juguetes ABC son los siguientes:

- Cumplir con el Marco de Ciberseguridad (CSF) del Instituto Nacional de Estándares y Tecnología (NIST). 
- Establecer un proceso más efectivo para garantizar el cumplimiento en los sistemas. 
- Fortalecer los controles del sistema.
- Implementar el principio de mínimo privilegio en la gestión de credenciales o tarjetas de identificación de usuarios. 
- Establecer políticas y procedimientos claros, que incluyan manuales de estrategia. 
- Asegurar el acatamiento de los requisitos de cumplimiento normativo. 

_________________________

### Lista De Control De Cumplimiento Normativo

Como resultado de la lista de control de cumplimiento al revisar las regulaciones y estándares normativos se obtuvo que se deben vigilar las siguientes normas:

- Reglamento General de Protección de Datos (RGPD): Proteger los datos de los residentes de la Unión Europea e informar sobre cualquier filtración.
Explicación: Juguetes ABC trabaja y recopila información de sus clientes en todo el mundo, esto incluye la Unión Europea.
- Estándares de seguridad de datos del sector de las tarjetas de pago (PCI DSS): Normatividad destinada a garantizar un entorno seguro para el uso de tarjetas de crédito.
Explicación: La empresa almacena, acepta, procesa y transmite información de tarjetas de crédito en línea y físicamente, por tal motivo debe cumplir con esta normativa.
- Controles de Sistemas y Organizaciones (SOC tipo 1, SOC tipo 2): Políticas de acceso de usuarios en los diferentes niveles de una organización.
Explicación: Es necesario que Juguetes ABC haga cumplir el acceso apropiado del personal, a fin de mitigar los riesgos y garantizar la seguridad de los datos.

________________________

### Evaluación De Controles

Dentro de la ciberseguridad los controles se agrupan en tres categorías principales: controles administrativos, controles técnicos y controles físicos.

Se determinaron los activos actuales de Juguetes ABC:

Entre los activos administrados por el departamento de TI se encuentran: 

- Equipos en las instalaciones para las necesidades comerciales en la oficina.  
- Equipos del personal: dispositivos de usuario final (computadoras de escritorio/portátiles, teléfonos inteligentes), estaciones de trabajo remotas, auriculares, cables, teclados, mouse, estaciones de acoplamiento, cámaras de vigilancia, etc.
- Gestión de sistemas, software y servicios: contabilidad, telecomunicaciones, bases de datos, seguridad, comercio electrónico y gestión de inventario.
- Acceso a Internet.
- Red interna.
- Gestión de acceso a proveedores.
- Servicios de alojamiento del centro de datos.  
- Retención y almacenamiento de datos.
- Lectores de tarjetas de identificación.
- Mantenimiento de sistemas heredados: sistemas obsoletos que requieren supervisión humana. 

Después de la auditoría de controles administrativos se determinaron los siguientes elementos de prioridad alta para implementar:

- Principios de mínimo privilegio
- Planes de recuperación ante incidentes
- Políticas de contraseñas
- Políticas de control de acceso
- Políticas de gestión de cuentas
- Separación de funciones

Se realiza la auditoria de controles técnicos y se determina de alta prioridad para implementar lo siguiente:

- Sistema de detección de intrusiones (IDS)
- Cifrado
- Copias de seguridad
- Gestión de contraseñas
- Software de antivirus (AV)
- Monitoreo manual, mantenimiento e intervención de sistemas heredados

Nota: Juguetes ABC ya disponía de algunos elementos tecnológicos para la seguridad como Firewalls.

Una vez realizada la auditoría de controles físicos se considera implementar con una prioridad elevada los siguientes elementos:

- Vigilancia del circuito cerrado de televisión (CCTV)
- Cerraduras
- Sistema de detección de incendios

_____________

### Memorando Para Las Partes Interesadas (Stakeholders)
<br>
<br>

<table class="tg"><thead>
  <tr>
    <td class="tg-73oq"><br><strong>PARA:</strong> Gerente de TI, Partes Interesadas (Stakeholders)<br><strong>DE:</strong> Diego Riaño<br><strong>ASUNTO:</strong> Hallazgos y recomendaciones de la auditoría interna de TI<br><br><br><strong>Respetados compañeros:</strong><br><br>En el siguiente resume se incluyes el alcance, los objeticos, los hallazgos críticos y las recomendaciones de la auditoría interna de Juguetes ABC.<br><br><strong>Alcance:</strong><br><br>•    Los siguientes sistemas están incluidos en el alcance:<br>Contabilidad, detección de puntos de conexión, firewalls, sistemas de detección de intrusiones, herramientas SIEM. Los sistemas se evaluaron en cuanto a:<br>      &nbsp&nbsp&nbsp• Permisos de usuario actuales.<br>      &nbsp&nbsp&nbsp• Controles implementados actuales<br>      &nbsp&nbsp&nbsp• Procedimientos y protocolos actuales.<br>•    Asegurar que los permisos de usuario, controles, procedimientos y protocolos actuales estén implementados conforme a los requisitos de cumplimiento de PCI DSS Y GDPR.<br>•    Asegurarse de que la tecnología actual se tenga en cuenta tanto para el acceso al hardware como al sistema.<br><br><strong>Objetivos:</strong><br><br>•    Cumplir con el CSF del NIST.<br>•    Establecer un mejor proceso para los sistemas a fin de garantizar que cumplan con las normas.<br>•    Fortalecer los controles del sistema.<br>•    Adaptarse al concepto de permisos mínimos en lo que respecta a la gestión de credenciales de usuario.<br>•    Establecer las políticas y procedimientos, incluidos los manuales de estrategias.<br>•    Asegurarse de que cumplen con los requisitos de cumplimiento.<br><br><strong>Hallazgos críticos:</strong><br><br>Se deben implementar los siguientes controles inmediatamente:<br><br>•    Se deben desarrollar e implementar múltiples controles para cumplir con los objetivos de la auditoría, incluidos:<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspControl de privilegios mínimos y separación de funciones.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspPlanes de recuperación ante desastres.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspPolíticas de contraseñas, control de acceso y administración de cuentas, incluida<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspla implementación de un sistema de administración de contraseñas.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspCifrado (para transacciones seguras en sitios web).<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspIDS.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspCopias de seguridad.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspSoftware antivirus.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspCCTV.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspCerraduras.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspMonitoreo, mantenimiento e intervención manuales para sistemas heredados.<br>&nbsp&nbsp&nbsp•    &nbsp&nbsp&nbspSistemas de detección y prevención de incendios.<br>•    Se deben desarrollar e implementar políticas para cumplir con los requisitos de cumplimiento de PCI DSS y GDPR.<br>•    Se deben desarrollar e implementar políticas para alinearse con la guía SOC1 y SOC2 relacionadas con las políticas de acceso de usuarios y la seguridad general de los datos.<br><br><strong>Otros hallazgos:</strong><br><br>Se deben implementar los siguientes controles cuando sea posible:<br><br>•    Caja fuerte con control de tiempo.<br>•    Iluminación adecuada.<br>•    Armarios con cerradura.<br>•    Señalización que indique el proveedor del servicio de alarma.<br><br><br><strong>Resumen y recomendaciones:</strong><br><br>Se recomienda trabajar de inmediato en los hallazgos críticos relacionados con el cumplimiento de PCI DSS y GDPR, ya que Juguetes ABC acepta pagos en línea de clientes de todo el mundo, incluida la UE. Además, dado que uno de los objetivos de la auditoría es adaptarse al concepto de permisos mínimos, se deben utilizar las pautas SOC1 y SOC2 relacionadas con las políticas de acceso de los usuarios y la seguridad general de los datos para desarrollar políticas y procedimientos adecuados. Tener planes de recuperación ante desastres y copias de seguridad también es fundamental porque respaldan la continuidad del negocio en caso de un incidente. La integración de un software de detección de intrusos y antivirus en los sistemas actuales respaldará nuestra capacidad de identificar y mitigar riesgos potenciales, y podría ayudar con la detección de intrusiones, ya que los sistemas heredados existentes requieren monitoreo e intervención manuales. Para proteger aún más los activos alojados en la única ubicación física de Juguetes ABC, se deben usar cerraduras y CCTV (circuito cerrado de televisión) para proteger los activos físicos (incluido el equipo) y para monitorear e investigar las posibles amenazas. Si bien no es necesario de inmediato, también es recomendable el uso de gabinetes con cerradura, sistemas de detección y prevención de incendios y señalización que indique el proveedor de servicios de alarma, esto mejorarán aún más la postura de seguridad de Juguetes ABC.<br><br><br>                                                     <br></td>
  </tr>
</thead></table>

