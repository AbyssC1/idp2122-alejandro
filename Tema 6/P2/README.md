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
