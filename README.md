# Práctica 3 - Creación de una Máquina Virtual de Azure

## Innovaccion Virtual (VII Edición) #IAWizards

### Semana 2 - Sesión 4
En esta práctica se crearon dos máquinas virtuales en la nube de Azure para posteriormente ejecutarlas y conectarlas entre sí.

-----------------------------------------------------------

#### Requerimientos
- Cuenta de Azure con suscripción.
- Algún programa que ejecute escritorios remotos como [Microsoft Remote Desktop](https://apps.microsoft.com/store/detail/microsoft-remote-desktop/9WZDNCRFJ3PS?hl=en-us&gl=US).

-----------------------------------------------------------

#### Pasos a seguir

1. Ingresar a portal.azure.com y busca ‘Virtual Machines’ y elige la opción de Máquinas virtuales. Enseguida, localizar la opción que diga ‘Crear’ y escoger ‘Máquina virtual de Azure’.

![P3I1](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2001.PNG)

2. Rellenamos los campos necesarios (Suscripción: Azure para estudiantes, Grupo de recursos: ‘Crear nuevo’ – Sesion4, Nombre de la máquina virtual: Sesion4-VMJ1, Región: EUA este o alguna otra región donde permita elegir el tamaño estándar, Imagen: Windows 10 Pro, Tamaño: Standard_DS1_v2). Nombre de usuario y contraseña deben ser creados aquí mismo, mientras que en la opción de ‘Seleccionar puertos de entrada’ se elige RDP.

![P3I2](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2002.PNG)

3. En el apartado de redes (la pestaña en la parte superior) dejamos todo por defecto, aunque se puede cambiar el factor de ‘Grupo de seguridad de red de NIC’ a Ninguno, pero existe probabilidad de que esto nos impida realizar los pasos siguientes, así que es mejor dejarlo como está. Le damos en ‘Revisar y crear’ y ‘Crear’.

![P3I3](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2003.PNG)

![P3I4](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2004.PNG)

4. Una vez creada la primera VM, se procede a crear otra, siguiendo los mismos pasos anteriores (Lo podemos poner en el mismo grupo de recursos o crear otro nuevo). Evidentemente, queremos que el nombre de la VM sea diferente (Sesion4-VMJ2 por ejemplo). En el apartado de red, se deberá asegurar de que ‘Red virtual’ se encuentre en la opción que diga vnet (por defecto, lleva el nombre de la red de la primera VM más el dato de “vnet”) es decir, ambas VM deben estar en el mismo grupo de red. Le damos ‘Revisar y crear’ y luego en ‘Crear’.

![P3I5](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2005.PNG)

5. Una vez creada la segunda VM, ingresamos desde la pantalla de inicio del portal de Azure al grupo de recurso e ingresamos a la primera VM creada. Le damos en ‘Conectar’ y en la opción de ‘RDP’ y le damos en donde diga ‘Descargar archivo RDP’.

![P3I6](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2006.PNG)

6. Deberemos tener instalado en nuestro equipo el programa ‘Remote Desktop’ (‘Escritorio remoto de Microsoft’). Una vez instalado este programa, abrimos el archivo que obtuvimos en el paso 5 con la aplicación de escritorio remoto. Nos pedirá las credenciales que creamos para nuestra primera máquina, por lo que las ingresamos.

![P3I7](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2007.PNG)

![P3I8](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2008.PNG)

7. Ya teniendo nuestra primera VM ejecutándose en el escritorio remoto, vamos al apartado de ‘Redes’ en el portal de Azure e ingresamos a ‘Red virtual/subred: (Nombre de nuestra red)’ y seleccionamos el apartado de ‘Dispositivos Conectados’.

![P3I9](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2009.PNG)

8. Copiamos la dirección IP que aparece para la segunda VM y abrimos en la primera VM el Powershell como administrador. En este escribimos el siguiente comando: `New-NetFirewallRule -DisplayName “Allow ICMPv4-In” -Protocol ICMPv4`, damos enter y escribimos lo siguiente: `mstsc /v:10.0.0.x` (aquí en x debe ir el número perteneciente al IP de la segunda VM). Este último comando permite abrir la segunda máquina virtual dentro de la primer máquina virtual.

![P3I10](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2010.PNG)

![P3I11](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2011.PNG)

![P3I12](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2012.PNG)

![P3I13](https://github.com/AlbertoSF99/Practica-3/blob/main/Images/Sesi%C3%B3n%204%20-%20P3%2013.PNG)

***Información Adicional:*** En el apartado de redes, para la primer VM es mejor no modificar nada. También, si no deja elegir el tamaño cuando se está creando la VM es buena idea cambiar de región a una donde si deje elegir el tamaño que requiramos. Es importante detener o eliminar las máquinas virtuales que ya no se ocupen.
