### Informe De Un Incidente Siguiendo El Marco CSF Del NIST
<br>
<br>

<table>
<tbody>
  <tr>
  <td><strong>Resumen</strong></td>
  <td>La empresa presentó un evento de seguridad cuando los servicios de red dejaron de funcionar. Se descubrió entonces que la interrupción fue causada por un ataque DDoS (ataque de denegación de servicio distribuido) debido a una inundación de paquetes ICMP. Se respondió deteniendo todos los servicios de red no críticos para reestablecer los servicios críticos de red.</td>
  </tr>
  <tr>
    <td><strong>Identificar</strong></td>
    <td>El agente de amenaza realizó un ataque de inundación ICMP afectando toda la red.</td>
  </tr>
  <tr>
    <td ><strong>Proteger</strong></td>
    <td>Se implementó una nueva regla en el firewall para poner un límite al número de paquetes ICMP entrantes y un sistema IDS/IPS para filtrar parte del tráfico sospechoso.</td>
  </tr>
  <tr>
    <td><strong>Detectar</strong></td>
    <td>Se ha configurado la verificación de la dirección IP de origen en el firewall, con el fin de comprobar direcciones falsas en los paquetes ICMP entrantes. También se ha implementado un software de monitoreo de red para detectar patrones de tráfico anormales.</td>
  </tr>
  <tr>
    <td><strong>Responder</strong></td>
    <td>En futuros eventos de seguridad, el personal de ciberseguridad aislará los sistemas afectados con el fin de prevenir nuevas interrupciones en la red. Se procurará habilitar los sistemas y servicios críticos que hallan sufrido interrupciones a causa del evento. Después de esto, se deberán analizar los registros de la red con el fin de verificar actividades sospechosas y anormales. Se informarán todos los sucesos a la dirección y a las autoridades legales correspondientes de ser necesario.</td>
  </tr>
  <tr>
    <td><strong>Recuperar</strong></td>
    <td>Los servicios de red deben restaurar a un estado normal después de un ataque DDoS por inundación de ICMP; estos ataques podrán bloquearse en un futuro con el uso del firewall. En este momento los servicios de red no críticos se detendrán para reducir el tráfico de red interno. Lo principal será restaurar los servicios de red críticos. Por último, cuando el flujo de paquetes ICMP haya agotado el tiempo de espera, todos los sistemas y los servicios de red no críticos serán reestablecidos.</td>
  </tr>
  <tr>
    <td><strong>Reflexiones/Notas</strong></td>
    <td>La mejora en la seguridad del sistema debe ser continua.</td>
  </tr>
</tbody></table>
