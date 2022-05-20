# Vagrant con VirtualBox

- Vagrant es una herramienta para la creación y configuración de entornos de desarrollo virtualizados.
- Originalmente se desarrolló para VirtualBox y para sistemas de configuración tales como Chef, Salt y Puppet. Sin embargo desde la versión 1.1 Vagrant es capaz de trabajar con múltiples proveedores, como VMware, Amazon EC2, LXC, DigitalOcean, etc.2
- Aunque Vagrant se ha desarrollado en Ruby se puede usar en multitud de proyectos escritos en otros lenguajes.

# Instalar Vagrant

- Instalar Vagrant. La instalación vamos a hacerla en una máquina real.
- Hay que comprobar que las versiones de Vagrant y VirtualBox son compatibles entre sí.
- vagrant version, para comprobar la versión actual de Vagrant.
- VBoxManage -v, para comprobar la versión actual de VirtualBox.
- Crear el alias va='vagrant'.

### Proyecto: Añadir cajas

Existen muchos repositorios desde donde podemos descargar la cajas de Vagrant (Imágenes o boxes). Incluso podemos descargarnos cajas de otros sistemas oprativos desde VagrantCloud Box List

OJO: Sustituir BOXNAME por ubuntu/bionic64

- vagrant box add BOXNAME, descargar la caja que necesitamos a través de  vagrant.
- vagrant box list, lista las cajas/imágenes disponibles actualmente en nuestra máquina.

> vagrant box list

> BOXNAME (virtualbox, 0)

# Directorio

Crear un directorio para nuestro proyecto. Donde XX es el número de cada alumno:

~~~
mkdir alejandro26-va1box.d
cd alejandro26-vagrant1
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/1%20Configuracion%20vagrant%20maquina%20real.png)

A partir de ahora vamos a trabajar dentro de esta carpeta.

Crear un fichero nuevo llamado Vagrantfile con el siguiente contenido:

~~~
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "alejandro26-va1box"
  config.vm.provider "virtualbox"
end
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/2%20Configuracion%20Vagrand.png)

# Comprobar

Vamos a crear una MV nueva y la vamos a iniciar usando Vagrant:

- Debemos estar dentro de alejandro26-va1box.d.
- vagrant up, para iniciar una nueva instancia de la máquina.
- vagrant ssh: Conectar/entrar en nuestra máquina virtual usando SSH.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/3%20Vagrant%20up.png)

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/4%20Vagrant%20ssh.png)

# Eliminamos la MV

- exit para salir fuera de la MV.
- Ahora estamos en la máquina real.
- vagrant halt, para apagar la máquina virtual.
- vagrant status, consultar el estado actual de la máquina virtual.
- vagrant destroy, para eliminar la máquina virtual (No los ficheros de configuración).

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/5%20exit%20vagrant%20halt%20vagrant%20status%20vagrant%20destroy.png)

# Proyecto: Redirección de puertos

Ahora vamos a hacer otro proyecto añadiendo redirección de puertos.

# Creamos los ficheros

En la máquina real:

- Crear carpeta alejandro26-va3port.d.
- Entrar en el directorio.
- Configurar Vagrantfile para usar nuestra caja BOXNAME y hostname = "alejandro26-vagrant3".
- Modificar el fichero Vagrantfile, de modo que el puerto 4226 del sistema anfitrión sea enrutado al puerto 80 del ambiente virtualizado.
- config.vm.network :forwarded_port, host: 4226, guest: 80.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/6%20mkdir%20alejandro26-va3port.d.png)

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/7%20Configuracion%20vagrant%20file%202.png)

Incluir en el fichero Vagrantfile las configuraciones necesarias para:

- La MV de VirtualBox debe tener el nombre vagrant26-port.
- La memoria RAM de la MV en VirtualBox debe ser de 2048 MiB.

Levantar la MV podemos hace vagrant up pero también time vagrant up para medir el tiempo que se tarda en levantar la MV. El añadir el comando time COMMAND delante de un comando nos calcula el tiempo que tarda en ejecutarse dicho comandos/programa (COMMAND).

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/8%20creamos%20fichero%20en%20maquina%20real.png)

# Entramos en la MV

- Entramos en la MV en la máquina virtual (vagrant ssh).
- Instalamos Apache2.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/9%20entramos%20con%20ssh%20y%20descargamos%20el%20vagrant.png)

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/10%20instalamos%20apache2.png)

# Comprobar

Para confirmar que hay un servicio a la escucha en 4567:

- Ir a la máquina real.
- vagrant port para ver la redirección de puertos de la máquina Vagrant.
- Abrir el navegador web con el URL http://127.0.0.1:4226. En realidad estamos accediendo al puerto 80 de nuestro sistema virtualizado.
- nmap -Pn localhost

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/11%20apache2.png)

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/12%20nmap.png)

# Proyecto: Suministro mediante shell script

Una de los mejores aspectos de Vagrant es el uso de herramientas de suministro. Esto es, ejecutar "una receta" o una serie de scripts durante el proceso de arranque del entorno virtual para instalar, configurar y personalizar un sin fin de aspectos del SO del sistema anfitrión.

- vagrant halt, apagamos la MV.
- vagrant destroy y la destruimos para volver a empezar.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/13%20apagar%20y%20destruir%20la%20mv.png)

# Crear ficheros

Ahora vamos a suministrar a la MV un pequeño script para instalar Apache.

Ejemplo:

~~~
20alejandro26-va4script.d
├── html
│   └── index.html
├── install_apache.sh
└── Vagrantfile
~~~

- Crear directorio alejandro26-va4script.d para nuestro proyecto.
- Entrar en dicha carpeta.
- Crear la carpeta html y crear fichero html/index.html con el siguiente contenido:

~~~
<h1>Proyecto Vagrant4 Scripting</h1>
<p>FECHA-ACTUAL</p>
<p>Nombre-del-alumnoXX</p>
~~~

- Crear el script install_apache.sh, dentro del proyecto con el siguiente contenido:

~~~
!/usr/bin/env bash
echo "[INFO] Script de instalación de apache2 de [alejandro26]"
apt update
apt install -y apache2
echo "[INFO] Fin del script: $(date)"
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/15%20script%20y%20index.png)

# Vagrantfile

Incluir en el fichero de configuración Vagrantfile lo siguiente:

- config.vm.hostname = "alejandro26-va4script"
- config.vm.provision :shell, :path => "install_apache.sh", para -  indicar a Vagrant que debe ejecutar el script install_apache.sh dentro del entorno virtual.
- config.vm.synced_folder "html", "/var/www/html", para sincronizar la carpeta exterior html con la carpeta interior. De esta forma el fichero "index.html" será visible dentro de la MV.

Incluir en el fichero Vagrantfile las configuraciones necesarias para:

- La MV de VirtualBox debe tener el nombre vagrant26-script.
- La memoria RAM de la MV en VirtualBox debe ser de 2048 MiB.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/14%20vagrant%20configuracion.png)

# Comprobamos

- vagrant up, para crear la MV. Podremos notar, al iniciar la máquina, que en los mensajes de salida se muestran mensajes que indican cómo se va instalando el paquete de Apache que indicamos.

- Para verificar que efectivamente el servidor Apache ha sido instalado e iniciado, abrimos navegador en la máquina real con URL http://127.0.0.1:4226

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/16%20comprobacion%20de%20que%20funciona%20el%20script.png)

# Proyecto: Suministro mediante Puppet

Puppet es un orquestador. Sirve para aprovisionar las máquinas locales o remotas sin usar scripting.

# Preparativos

- Crear directorio nombre-alumnoXX-va5puppet.d como nuevo proyecto Vagrant.

- Modificar el archivo Vagrantfile de la siguiente forma:

~~~
Vagrant.configure("2") do |config|
  ...
  config.vm.hostname = "alejandro26-va5puppet"
  ...
  # Nos aseguramos de tener Puppet en la MV antes de usarlo.
  config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y puppet"

  # Hacemos aprovisionamiento con Puppet
  config.vm.provision "puppet" do |puppet|
    puppet.manifest_file = "alejandro26.pp"
  end
 end
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/17%20configuracion%20vagrant.png)

- Crear la carpeta manifests.
- Crear el fichero manifests/alejandro26.pp, con las órdenes/instrucciones Puppet necesarias para instalar el software que elijamos. Ejemplo:

~~~
package { 'neofetch':
  ensure => 'present',
}
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/18%20alejandro26pp.png)
