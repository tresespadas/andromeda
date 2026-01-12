# Instalación y configuración de un dominio básico AD con Windows Server 2019
## Red LAN del servidor
Para la posterior unión del cliente al servidor se debe modificar el adaptador de red destinado a LAN.
![Red LAN del servidor](../../assests/images/aso/ud6/act1/adaptador_red_servidor_wserver_lan.png)

## Cambio de nombre del servidor
A continuación, se muestra el cambio de nombre del servidor. Requiere de un reinicio posterior.
![Cambio de nombre del servidor](../../assests/images/aso/ud6/act1/cambio_nombre_server.png)

## Instalación del rol "Servicios de dominios de Active Directory"
Administrar > Agregar roles y características > Instalación basada en características o roles > Seleccionar el servidor > Seleccionar "Servicios de dominio de Active Directory" y "Servidor DNS" > Confirmar instalación
![Administrar y agregar roles](../../assests/images/aso/ud6/act1/administrar_agregar_roles.png)
![Administrar y agregar roles 2](../../assests/images/aso/ud6/act1/administrar_agregar_roles_2.png)
![Administrar y agregar roles 3](../../assests/images/aso/ud6/act1/administrar_agregar_roles_3.png)
![Administrar y agregar roles 4](../../assests/images/aso/ud6/act1/administrar_agregar_roles_4.png)
![Rol de Active Directory](../../assests/images/aso/ud6/act1/rol_active_directory.png)
![Rol de DNS](../../assests/images/aso/ud6/act1/rol_dns.png)
![Rol de AD y DNS](../../assests/images/aso/ud6/act1/rol_ad_dns.png)
![Rol de AD y DNS 2](../../assests/images/aso/ud6/act1/rol_ad_dns_2.png)
![Instalación del rol de AD](../../assests/images/aso/ud6/act1/instalacion_rol_ad.png)
![Instalación del rol de DNS](../../assests/images/aso/ud6/act1/instalacion_rol_dns.png)
![Confirmación roles AD y DNS](../../assests/images/aso/ud6/act1/confimacion_instalacion_roles_ad_dns.png)
![Instalando roles AD y DNS](../../assests/images/aso/ud6/act1/instalando_roles_ad_dns.png)

## Promover servidor a controlador de dominio
Una vez terminada la instalación de los roles > Promover este servidor a contrlador de dominio > Configuración de implementación > Agregar nuevo bosque > Opciones de controlador de dominio > Establecer una contraseña DSRM > Opciones de DNS > Nombre de NetBIOS
![Promover a DC](../../assests/images/aso/ud6/act1/promover_dc.png)
![Password DSRM](../../assests/images/aso/ud6/act1/password_dsrm.png)
![Opciones de DNS](../../assests/images/aso/ud6/act1/delegacion_dns.png)
![Nombre de NetBIOS](../../assests/images/aso/ud6/act1/nombre_netbios.png)

### Antes del siguiente paso, se debe inicializar el disco E:\
Administrador de discos > Botón derecho para inicializar el disco > Formato y tamaño
![Administrador de discos 1](../../assests/images/aso/ud6/act1/admin_discos.png)
![Administrador de discos 2](../../assests/images/aso/ud6/act1/admin_discos_2.png)
![Administrador de discos 3](../../assests/images/aso/ud6/act1/admin_discos_3.png)
![Administrador de discos 4](../../assests/images/aso/ud6/act1/admin_discos_4.png)
![Administrador de discos 5](../../assests/images/aso/ud6/act1/admin_discos_5.png)
![Administrador de discos 6](../../assests/images/aso/ud6/act1/admin_discos_6.png)
![Administrador de discos 7](../../assests/images/aso/ud6/act1/admin_discos_7.png)
![Administrador de discos 8](../../assests/images/aso/ud6/act1/admin_discos_8.png)

Continuando desde NetBIOS > Rutas de acceso > Script de PowerShell de instalación > Comprobación de requisitos previos > Reinicio obligatorio > Comprobación
![Rutas de acceso](../../assests/images/aso/ud6/act1/rutas_acceso.png)
![Script de PowerShell](../../assests/images/aso/ud6/act1/script_ps.png)
![Comprobación de requisitos previos](../../assests/images/aso/ud6/act1/comprobacion_requisitos_previos.png)
![Reinicio](../../assests/images/aso/ud6/act1/reinicio.png)
![Comprobación de AD](../../assests/images/aso/ud6/act1/comprobacion_final_ad_ds.png)
![Comprobación de AD 2](../../assests/images/aso/ud6/act1/comprobacion_final_ad_ds_2.png)

NOTA: Contraseña DSRM:
```
WindowsServer2019!$
```

NOTA: Script de PowerShell de instalación
```ps1
#
# Script de Windows PowerShell para implementación de AD DS
#

Import-Module ADDSDeployment
Install-ADDSForest `
-CreateDnsDelegation:$false `
-DatabasePath "E:\NTDS" `
-DomainMode "WinThreshold" `
-DomainName "midominio.local" `
-DomainNetbiosName "MIDOMINIO" `
-ForestMode "WinThreshold" `
-InstallDns:$true `
-LogPath "E:\NTDS" `
-NoRebootOnCompletion:$false `
-SysvolPath "E:\SYSVOL" `
-Force:$true
```

## Unir cliente Windows 10 al servidor
En primer lugar, se debe incluir el cliente a la red LAN del servidor (192.168.10X.Y)
![Adaptador de red cliente W10](../../assests/images/aso/ud6/act1/adaptador_red_cliente_w10_lan.png)

### Antes de continuar con el siguiente paso, se debe crear una unidad organizativa y un usuario (al menos)
En el servidor > Herramientas > Usuarios y equipos de Active Directory > Crear unidad organizativa > Crear un usuario y su contraseña
![Usuarios y equipos AD](../../assests/images/aso/ud6/act1/usuarios_equipos_ad.png)
![Crear UO](../../assests/images/aso/ud6/act1/creado_uo.png)
![Crear Usuario](../../assests/images/aso/ud6/act1/creando_usuario.png)
![Password usuario](../../assests/images/aso/ud6/act1/password_usuario.png)

De nuevo en el servidor, se cambia el nombre del equipo y  se añade al dominio. En Configuración > Sistema > Configuración avanzada del sistema > Nombre del equipo > Cambiar
![Unir cliente a dominio](../../assests/images/aso/ud6/act1/unir_cliente_dominio.png)
![Unir cliente a dominio 2](../../assests/images/aso/ud6/act1/unir_cliente_dominio_2.png)
![Unir cliente a dominio 3](../../assests/images/aso/ud6/act1/unir_cliente_dominio_3.png)

Después de reiniciar...
![Iniciar sesión](../../assests/images/aso/ud6/act1/iniciando_sesion_dominio.png)
![Iniciar sesión 2](../../assests/images/aso/ud6/act1/iniciando_sesion_dominio_2.png)

Comprobación el servidor
![Comprobación en el servidor](../../assests/images/aso/ud6/act1/comprobacion_servidor_equipo_cliente.png)
