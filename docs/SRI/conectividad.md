# Conectividad con Internet y red local

## Debian
### Comprobando interfaces
```
ip link show
```
### Apagando algunas interfaces
```
ip link set dev eth1 down
...
```
### Archivo de configuracion
```
/etc/network/interfaces
```
### Reinicio de la red
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
