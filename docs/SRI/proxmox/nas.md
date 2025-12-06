# NAS vía NFS
## Máquina dedicada al NAS
- Nueva máquina para el NAS
- Creación de una nueva red para el NAS
- Particionado de disco
```bash
cfdisk /dev/sdb
```
- Formateado de la partición
```bash
mkfs -t ext4 -L "hdNFS" /dev/sdb1
```
- Creación de punto de montaje y montaje
```bash
mkdir -p /media/hdNFS
mount -t auto /dev/sdb1 /media/hdNFS/
```
- Instalación de paquetes
```bash
apt install nfs-kernel-server
```
- Edición del /etc/exports
```bash
/media/hdNFS 10.200.0.0/24(rw,sync,no_subtree_check)
```
- Reinicio del demonio
```bash
exportfs -av
```
- Permisos de la carpeta
```bash
chmod 777 /media/hdNFS -R
```
## En el cluster
Datacenter > Storage > Add NFS
![Instalación NAS](../../assests/images/instalacion_nas.png)
