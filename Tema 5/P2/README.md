<h1>  Unir cliente GNU/Linux a un dominio Windows </h1>

<h2> Introducción </h2>
<li>HORA: La fecha/hora y la zona horaria de la máquina debe ser igual que la del Windows Server (PDC). que tenemos en el PDC (Windows Server).</li>
<li>NOBRE DEL EQUIPO: "hernandez26g".
<li>VIRTUALBOX: GNU/Linux y PDC, deben estar en la misma red, por lo que es aconsejable configurar la red de las máquinas virtuales en modo puente (El modo "Red interna" también funcionará bien).
<li>Interfaz de RED: Recordar que las máquinas (Servidor y cliente) deben tener la configuración de red estática. Configurar la red con IP estática.
<li>Servidores DNS: Configurar el cliente GNU/Linux para tener dos servidores DNS. Esto es, DNS1=172.18.26.21, y DNS2=1.1.1.1.
<p>Realizar la comprobación del DNS mediante la ejecución de
<li>host DOMINIO-DEL-PDC, por ejemplo "host hernandez26dom.curso2022".
<li>host NOMBRE-EQUIPO-PDC.NOMBRE-DOMINIO, por ejemplo "host alejandroWS.hernandez26dom.curso2022"
<li>host www.nba.com

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/Comprobaciones.png)

<h2>Unirse al dominio</h2>
Usar Yast para unir la MV al dominio del PDC.

<li>Yast -> Pertenencia a dominio de Windows (Unirse a un dominio)
<li>Poner el nombre largo del dominio. Por ejemplo "hernandez26.curso2022".
<li>Activar la Autenticación SMB.
<li>Activar Crear home del usuario.
<li>Pulsamos "Aceptar". Es posible que se instalen algunos paquetes que hacen falta para seguir.

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/1Unirse%20al%20dominio.png)
   
<h2>Abrir sesión en el cliente</h2>
<li>Asegurarse que los usuarios del dominio no tienen restricciones de inicio de sesión.

<li>Iniciar sesión en el equipo GNU/Linux usando un usuario del dominio.

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/3Uniser%20al%20dominio%20con%20administrador.png)
   
<li> Entramos en el dominio
   
![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/4Conectado%20correctamente.png) 
   
<p>Una vez iniciada la sesión ejecutar los comandos de comprobación:</p>

<li>whoami, esto debe devolver DOMINIO\USERNAME que ha iniciado sesión.
<li>pwd, para consultar el directorio actual.
<li>cat /etc/passwd | grep USERNAME, esto debe devolver vacío, indicando que el usuario no está definido como usuario local, por tanto, debe ser un usuario del dominio.

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/7Comprobaciones%20dentro%20del%20dominio%20de%20opensuse.png) 
   
<h2>Recursos compartidos</h2>
   
<p>Podemos acceder al recurso compartido del Window Server (PDC) de la siguiente forma:

<li>Iniciar un explorador de archivos.
<li>Escribir lo siguiente en la barra de ruta que está en la parte superior, por ejemplo: smb://172.18.26.21/perfiles$/
   <p> <code> Las barras \\ se cambian a // ya que es linux, en este caso OpenSuse. </code> </p>
   
 ![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P2/8Entra%20el%20V5.png) 
   
   
