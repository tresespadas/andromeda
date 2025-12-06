# Instalación y configuración de NFS
## Instalación de paquetes para NFS
En el servidor
```
sudo apt-get install nfs-kernel-server nfs-common rpcbind
```
Reinicio después de la instalación
```
sudo reboot
```

## Compartir una carpeta
Permisos y owners
```
sudo mkdir -p /acabelloaguilar
sudo chown -R nobody:nogroup /acabelloaguilar/
sudo chmod 777 /acabelloaguilar/
```

## Archivo /etc/exports
```
/acabelloaguilar 192.168.104.0/24(rw,sync,no_subtree_check)
```
Comprobación del archivo /etc/exports
```
sudo exportfs -a
```
Reinicio del servicio
```
sudo systemctl restart nfs-server.service
sudo systemctl status nfs-server.service
```

## Acceso desde cliente Linux
Instalación del paquete nfs-common
```
sudo apt install nfs-common
```
Creación del punto de montaje y permisos
```
sudo mkdir -p /mnt/nfs/acabelloaguilar
sudo chmod 777 /mnt/nfs -R
```
Montaje de la carpeta compartida
```
sudo mount 192.168.104.10:/acabelloaguilar /mnt/nfs/acabelloaguilar
```

## Montaje automático en Linux
Editando el arhivo /etc/fstab
```
192.168.104.10:/acabelloaguilar /mnt/nfs/acabelloaguilar nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

## Montaje en Windows
Habilitar Cliente NFS
![Opciones NFS Windows](../../assests/images/opciones-nfs-windows.png)

Montaje de la carpeta compartida vía CMD
```
mount \\192.168.104.10\acabelloaguilar Y:
```
