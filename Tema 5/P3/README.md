<h1>Políticas o directivas de grupo </h1>
  <h2>1. Aplicar directivas de Usuario</h2>
    <h3>1.1 Crear las OU (Unidad Organizativa)</h3>
       <li>Ir a la MV PDC. </li>
       <li>Por seguridad, antes de empezar la práctica vamos a crear un "snapshot" (instantánea) de la máquina virtual. </li>
         <li>Abrir la herramienta de gestión de "Usuarios y equipos del Active Directory". </li>
           <li>En el panel izquierzo, hacer click derecho sobre el nombre de nuestro dominio. Elegir Nuevo -> Crear Unidad Organizativa </li>
      <li>      Crear las OU (Unidades Organizativas) siguientes: jedis26 y siths26. </li>
  <li>Los usuarios (obiwan y yoda) que teníamos creados en Usuarios, los movemos a la OU de jedis.</li>
  <li>Los usuarios (maul y vader) que teníamos creados en Usuarios, los movemos a la OU de siths.</li><p></p>
  
  ![Comprobaciones](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P3/1%20Unidades%20Organizativa%20jedis%20y%20siths.png)
  
  <h2>1.2 Crear GPO's</h2>
  
<li>Ir a Herramientas -> Administración de directivas de grupo </li>
<li>Dentro de la OU de los jediXX -> Botón derecho -> crear la GPO gpo_jedi26. </li>
<li>Dentro de la OU de los sithXX -> Botón derecho -> crear la GPO gpo_sith26. </li><p></p>
  
![GPO_jedi26](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P3/2%20Creacion%20de%20gpo_jedis.png)


![GPO_sith26](https://github.com/AbyssC1/idp2122-alejandro/blob/main/Imagenes/T5%20P3/3%20Creacion%20de%20gpo_siths.png)


<h2>1.3 Personalizar cada GPO de forma diferente</h2>

<li>No buscar archivos</li>
<li>No buscar programas</li>
<li>Quitar el menú Ejecutar del menú Inicio</li>
<li>Quitar el icono de Red del menú inicio</li>
<li>Quitar icono de Red</li>
<li>Quitar Conexiones de red del menú Inicio</li><p></p>

<p>En la sección Configuración de usuario / Directivas / Plantillas administrativas / Panel de control (User configuration / Administrative Templates / Control Panel)</p>

<code><li>Prohibir el acceso al Panel de control</li></code>
<p>En la sección Configuración de usuario / Directivas / Plantillas administrativas / Escritorio ( User configuration / Administrative Templates / Active Desktop)</p>

<code><li>Ocultar el icono Ubicaciones de red del escritorio.</li></code>
<p>En la sección Configuración de usuario / Directivas / Plantillas administrativas / Componentes de Windows / Explorador de Windows (User configuration / Administrative Templates / Windows Components / Windows Explorer)</p>

<li>Ocultar estas unidades específicas en Mi PC (Hide these specified drives in My Computer) o Impedir el acceso a las unidades desde Mi PC (Prevent Access to drives from my computer). Elegir un combinación adecuada como bloquear las unidades A y B (Restrict A y B drives only).</li>
<li>Quitar <Conectar a unidad de red> y <Desconectar de unidad de red></li>
  
