# Preparación vagrant + libvirt + QEMU/KVM

## QEMU/KVM + libvirt
```
sudo apt install qemu-system libvirt-clients libvirt-daemon-system
```
```
sudo apt install virtinst
```
En Arch
```
sudo pacman -S qemu-full libvirt virt-install
```
```
sudo usermod -aG libvirt $USER
```
## vagrant
En Arch
```
yay -S vagrant
```

```
vagrant plugin install vagrant-libvirt
vagrant up --provider=libvirt
```
## virsh
### Comprobación de las redes existentes
```
virsh net-list --all
```
### Creación de la red interna
```
cat <<EOF > /tmp/red-interna.xml
<network>
  <name>red-interna</name>
  <forward mode='none'/>
  <ip address='10.20.30.1' netmask='255.255.255.0'/>
</network>
EOF
```
```
sudo virsh net-define /tmp/red-interna.xml
sudo virsh net-autostart red-interna
sudo virsh net-start red-interna
```
