## Lectura De Enrutamiento Malicioso
<br>

Para este ejemplo se definen los siguientes parámetros:

- pc.deprueba = la máquina desde la cual se examina lo que está ocurriendo.
- sitiowebcorporativo.com = la página web de la empresa
- lawebfalsa.com = la página a la que se está redirigiendo el tráfico de la web corporativa.

<strong>
En la empresa se presentaron reclamos de clientes informando que el sitio web corporativo los estaba llevando a un sitio diferente luego de solicitar una actualización del navegador, por lo cual se procedió a realizar un estudio de los registros de tráfico utilizando la herramienta tcpdump, los cuales se muestran a continuación:
</strong>
<br>
<br>

<table border="1"><thead>
  <tr>
    <td class="tg-0pky">14:18:32.192571 IP pc.deprueba.52444 &gt; dns.google.domain: 35084+ A? sitiowebcorporativo.com. (24)<br>14:18:32.204388 IP dns.google.domain &gt; pc.deprueba.52444: 35084 1/0/0 A 203.0.113.22 (40)<br><br><br>14:18:36.786501 IP pc.deprueba.36086 &gt; sitiowebcorporativo.com.http: Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0<br>14:18:36.786517 IP sitiowebcorporativo.com.http &gt; pc.deprueba.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0<br>14:18:36.786529 IP pc.deprueba.36086 &gt; sitiowebcorporativo.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0<br>14:18:36.786589 IP pc.deprueba.36086 &gt; sitiowebcorporativo.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1<br>14:18:36.786595 IP sitiowebcorporativo.com.http &gt; pc.deprueba.36086: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0<br>…&lt;a lot of traffic on the port 80&gt;... <br><br><br>14:20:32.192571 IP pc.deprueba.52444 &gt; dns.google.domain: 21899+ A? lawebfalsa.com. (24)<br>14:20:32.204388 IP dns.google.domain &gt; pc.deprueba.52444: 21899 1/0/0 A 192.0.2.17 (40)<br><br>14:25:29.576493 IP pc.deprueba.56378 &gt; lawebfalsa.com.http: Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0<br>14:25:29.576510 IP lawebfalsa.com.http &gt; pc.deprueba.56378: Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0<br>14:25:29.576524 IP pc.deprueba.56378 &gt; lawebfalsa.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0<br>14:25:29.576590 IP pc.deprueba.56378 &gt; lawebfalsa.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 73: HTTP: GET / HTTP/1.1<br>14:25:29.576597 IP lawebfalsa.com.http &gt; pc.deprueba.56378: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0<br>…&lt;a lot of traffic on the port 80&gt;...<br></td>
  </tr>
</thead></table>
<br>

### Ahora se comienza el análisis de los registros:

<br>

> 14:18:32.192571 IP **pc.deprueba.52444 > dns.google.domain:** 35084+ A? **sitiowebcorporativo.com.** (24)
> 14:18:32.204388 IP **dns.google.domain > pc.deprueba.52444:** 35084 1/0/0 A 203.0.113.22 (40)

Lo que muestran los registros DNS y HTTP es que desde la máquina de origen (**pc.deprueba**) utiliza el puerto **52444** para enviar la solicitud al DNS (**dns.google.domain**) para encontrar la URL de **sitiowebcorporativo.com** que es **203.0.113.22**. 

> 14:18:36.786501 IP **pc.deprueba.36086 > sitiowebcorporativo.com.http: Flags [S]**, seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0
>
> 14:18:36.786517 IP sitiowebcorporativo.com.http > pc.deprueba.36086: **Flags [S.]**, seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0

En esta sección se muestra que el computador envía una solicitud de conexión (**Flags [S]**) usando el puerto **36086** directamente al destino (**sitiowebcorporativo.com.http**). El sufijo .http es el número de puerto (**normalmente 80**). La respuesta muestra que el destino recibió la solicitud de conexión (**Flags [S.]**). 


> 14:18:36.786589 IP pc.deprueba.36086 > **sitiowebcorporativo.com.http:** Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: **HTTP: GET / HTTP/1.1**

En el registro aparece **HTTP: GET / HTTP/1.1** que muestra al navegador solicitando datos de **sitiowebcorporativo.com** mediante el uso del protocolo **HTTP** versión **1.1**. Este puede ser el archivo que informaron los clientes en sus reclamos.

> 14:20:32.192571 IP **pc.deprueba.52444 > dns.google.domain**: 21899+ A? lawebfalsa.com. (24)
>
> 14:20:32.204388 IP **dns.google.domain > pc.deprueba.52444:** 21899 1/0/0 A **192.0.2.17** (40)
>
> 14:25:29.576493 **IP pc.deprueba.56378 > lawebfalsa.com.http:** Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0
>
> 14:25:29.576510 IP **lawebfalsa.com.http > pc.deprueba.56378: Flags** [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0



Es entonces cuando ocurre un cambio repentino en los registros, el tráfico se enruta desde **pc.deprueba** al servidor DNS utilizando de nuevo el puerto **52444** para realizar la resolución de nombres (**pc.deprueba.52444 > dns.google.domain**); esta vez el servidor DNS enruta el tráfico a la dirección **IP 192.0.2.17** y a su URL asociada **lawebfalsa.com**, por último se realiza la conexión entre **lawebfalsa.com** y **pc.deprueba** a través del puerto **.56378**. Es decir, el tráfico cambia a una ruta entre el computador de origen y el sitio web falso.



