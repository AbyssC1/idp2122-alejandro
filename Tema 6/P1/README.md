<h1>Instalación desatendida</h1>
<h2>Instalación desatendida con autoyast</h2>
<h2>Preparativos</h2>

<li>Crear una MV1 nueva o usar una que ya tengamos con SO OpenSUSE.</li>
<li>OJO: La MV deben tener configurada la opción de BIOS. NO UEFI.</li>
<li>El proceso de instalación desatendida con UEFI debe revisarse porque es diferente.</li>
  <p>Personalizamos nuestra máquina con los siguientes cambios:</p>
<li>Nombre de máquina hernandez26y.</li>
<li>Instalamos paquetes que no vengan por defecto preinstalados. Por ejemplo: evince, inkscape, vlc (Prueba los programas para que los conozcas).</li>
<li>Creamos usuario alejandroG1.</li>

<h2>Fichero de respuestas</h2>
<h2>Crear el fichero de respuestas</h2>

<li>Instalamos la herramienta Autoyast (Paquetes autoyast2, autoyast2-installation).</li>
<li>Ir a Yast -> Autoinstallation Cloning System (Por el terminal es igual usando el comando /sbin/yast2 clone_system).</li>
<li>El perfil se guarda en /root/autoinst.xml.</li>
<li>cp /root/autoinst.xml /root/alejandro26.xml. Hacemos una copia de seguridad del perfil.</li></p>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/1%20clonando%20el%20sistema%20xml.png)

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/2%20Copia%20de%20xml%20alejandro.png)

<h2>Copiar fichero XML en pendrive</h2>

<p>Vamos a copiar el fichero de control en un USB:</p>

<li>Estamos en la MV1.</li>
<li>Poner el pendrive y montarlo por el entorno gráfico.</li>
<li>Abrir un terminal como root.</li>
<li>df -hT |grep media, consultar la ruta donde está montado el USB.</li>
<li>cp /root/alejandro26.xml /run/media/..., copiar el archivo XML en la ruta del USB.</li>
<li>Podemos apagar la MV1.</li></p>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/3%20copiamos%20el%20xml%20en%20el%20usb.png)

<h2>Comprobamos</h2>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/4%20comprobacion%20de%20la%20copia.png)

<h2>Instalación desatendida desde USB</h2>

<p>Ya tenemos nuestro fichero XML de respuestas en un pendrive. Ahora vamos a realizar una instalación desatendida en una nueva máquina MV2.</p>

<li>En VirtualBox crear una MV2 nueva, con un tamaño de disco duro similar a la MV1.</li>
<li>Configurar MV2 para acceder al pendrive USB, igual que hicimos con la MV1.</li>
<li>Ponemos el DVD (ISO) de instalación de OpenSUSE en la MV2.</li>
<li>Seleccionamos nuestra MV2 y configuración -> USB -> Añadir. Elegimos nuestro USB y aceptamos. Ahora debe estar montado el pendrive con el fichero de control XML en MV2.</li>
<li>Iniciar la MV2.</li></p>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/4.2%20Comprobamos%20en%20bios%20que%20instalamos%20el%20xml.png)

<li>Elegimos Instalación.</li>
<li>Completar Opciones de arranque con: autoyast=usb:///alejandro26.xml</li>

<h2>Comprobamos</h2>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/5%20instalando%20autoyast%20con%20el%20xml.png)


<h2>Software para editar ficheros ISO</h2>

<li>Ir la máquina real.</li>
<li>Debemos tener instalado el programa Power-iso en la máquina real. Power-iso es un programa para modificar el contenido de ficheros ISO.</li>

<h2>Preparamos la ISO</h2>
<li>Copiar el fichero alejandro26.xml en la máquina real.</li>
<li>Iniciamos Power-iso y abrimos el fichero ISO de OpenSUSE.</li>
<li>Añadir el fichero XML dentro del directorio raíz de la ISO.</li></p>

![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/7%20comprobacion%20del%20xml%20en%20el%20iso.png)


<h2>Instalación desatendida desde la ISO</h2>


![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P1/6%20instalando%20con%20el%20xml.png)



