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
