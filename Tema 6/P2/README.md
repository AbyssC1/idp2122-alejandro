# Vagrant con VirtualBox

-Vagrant es una herramienta para la creación y configuración de entornos de desarrollo virtualizados.
-Originalmente se desarrolló para VirtualBox y para sistemas de configuración tales como Chef, Salt y Puppet. Sin embargo desde la versión 1.1 Vagrant es capaz de trabajar con múltiples proveedores, como VMware, Amazon EC2, LXC, DigitalOcean, etc.2
-Aunque Vagrant se ha desarrollado en Ruby se puede usar en multitud de proyectos escritos en otros lenguajes.

# Instalar Vagrant

-Instalar Vagrant. La instalación vamos a hacerla en una máquina real.
-Hay que comprobar que las versiones de Vagrant y VirtualBox son compatibles entre sí.
-vagrant version, para comprobar la versión actual de Vagrant.
-VBoxManage -v, para comprobar la versión actual de VirtualBox.
-Crear el alias va='vagrant'.

### Proyecto: Añadir cajas

Existen muchos repositorios desde donde podemos descargar la cajas de Vagrant (Imágenes o boxes). Incluso podemos descargarnos cajas de otros sistemas oprativos desde VagrantCloud Box List

OJO: Sustituir BOXNAME por ubuntu/bionic64

vagrant box add BOXNAME, descargar la caja que necesitamos a través de vagrant.
vagrant box list, lista las cajas/imágenes disponibles actualmente en nuestra máquina.

> vagrant box list

> BOXNAME (virtualbox, 0)

# 1.2 Directorio

Crear un directorio para nuestro proyecto. Donde XX es el número de cada alumno:

~~~
mkdir alejandro26-va1box.d
cd alejandro26-vagrant1
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/Mediana/1%20Configuracion%20vagrant%20maquina%20real%20(Mediana).jpg)

A partir de ahora vamos a trabajar dentro de esta carpeta.

Crear un fichero nuevo llamado Vagrantfile con el siguiente contenido:

~~~
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "alejandro26-va1box"
  config.vm.provider "virtualbox"
end
~~~

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/Mediana/2%20Configuracion%20Vagrand%20(Mediana).jpg)

# 1.3 Comprobar

Vamos a crear una MV nueva y la vamos a iniciar usando Vagrant:

-Debemos estar dentro de nombre-alumnoXX-va1box.d.
-vagrant up, para iniciar una nueva instancia de la máquina.
-vagrant ssh: Conectar/entrar en nuestra máquina virtual usando SSH.

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/Mediana/3%20Vagrant%20up%20(Mediana).jpg)

![alt text](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T6%20P2/Mediana/4%20Vagrant%20ssh%20(Mediana).jpg)
