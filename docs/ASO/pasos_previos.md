# Pasos previos

## Creación de nuevo usuario
```
sudo adduser <nombre>
sudo usermod -aG sudo,adm <nombre>
```
## Cambio del hostname
```
sudo hostnamectl set-hostname <hostname>
```
## Comprobación IPs máquina
```
ip -br a
```
## Editar archivo de red /etc/netplan/99_config.yaml
```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: true
    ens19:
      addresses:
        - 192.168.104.10/24
```
## Configurar la hora y zona horaria de Madrid
```
sudo timedatectl set-timezone "Europe/Madrid"
```
