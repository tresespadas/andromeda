# Configuración LDAP Servidor

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
## Añadir un fichero al directorio
```
sudo ldapadd -x -D cn=admin,dc=iesguadalpena,dc=es -W -f <nombre-fichero>.ldif
```
## Buscar elementos en el directorio
```
sudo ldapsearch -xLLL -b "dc=iesguadalpena,dc=es" <condicion> <atributo-que-mostrar>
```
## Borrado de elementos en el directorio
```
sudo ldapdelete -x -W -D "cn=admin,dc=iesguadalpena,dc=es" <dn-que-borrar>
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
## Editar archivo /etc/ldap/ldap.conf
```
BASE	dc=nombre-dominio,dc=extension
URI	ldap://<IP>:389
```
