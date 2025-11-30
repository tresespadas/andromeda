# Configuración LDAP Cliente

## Actualización del sistema
```
sudo apt update
sudo apt dist-update
```
## Instalación de paquetes necesarios
```
sudo apt-get install libnss-ldap libpam-ldap ldap-utils
```
## Ajustes en /etc/nsswitch.conf
Establecer búsquedas de passwd, group, shadow y gshadow en ldap.
## Ajustes en /etc/pam.d/common-password
Eliminar use_authok
## Ajustes en /etc/pam.d/common-session
Añadir la línea:
```
session optional	pam_mkhomedir.so skel=/etc/skel umask=077
```
## Habilitar el servicio libnss-ldap
```
sudo systemctl start libnss-ldap.service
```
## Habilitar el inicio de sesión en modo gráfico
```
sudo apt install nslcd
```
## Acceso a LAM a través del navegador
```
http://<IP-Servidor>:389/lam
```
