# Configuración Servidor LDAP

## Actualización del sistema
```
sudo apt update
sudo apt dist-update
```
## Resolución de host en /etc/hosts
```
#<IP> <hostname>.<dominio> <hostname>
192.168.104.10 ldap-server.iesguadalpena.es ldap-server
```
## Instalación del software LDAP
```
sudo apt install slapd ldap-utils -y
```
## Habilitar servicio al encender el servidor
```
sudo systemctl enable slapd.service
```
## Fichero ejemplo: Unidad organizativa
```
dn: ou=usuarios,dc=aula,dc=local
objectClass: organizationalUnit
ou: usuarios

dn: ou=grupos,dc=aula,dc=local
objectClass: organizationalUnit
ou: grupos
```
