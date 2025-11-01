# Conectividad con Internet y red local

## Básico
### Comprobando interfaces
```
ip link show
```
### Apagando algunas interfaces
```
ip link set dev eth1 down
```
### Mostrando IPs
```
ip -4 -br a
```
## Debian
### Archivo de configuracion
```
/etc/network/interfaces
```
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# Alternative: DHCP configuration for eth0
# auto eth0
# iface eth0 inet dhcp

# The primary network interface (static IP example)
auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    # Optional: DNS servers
    dns-nameservers 8.8.8.8 8.8.4.4
    dns-search example.com
```
### Aplicación de los cambios
```
sudo systemctl restart networking
```

## Ubuntu
### Archivo de configuracion
```
sudo vim /etc/netplan/50-cloud-init.yaml
```

```
network:
  version: 2
  ethernets:
    ens18:
      dhcp4: true

    ens19:
      dhcp4: false
      addresses:
        - 192.168.104.10/24
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

```
### Aplicación de los cambios
```
sudo netplan apply
```
