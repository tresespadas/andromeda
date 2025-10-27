# Preparación vagrant + libvirt + QEMU/KVM

## QEMU/KVM + libvirt
### QEMU/KVM + libvirt
```
sudo apt install qemu-system libvirt-clients libvirt-daemon-system
```
```
```
```
sudo apt install virtinst
```
En Arch
```
sudo pacman -S qemu libvirt virt-install
```
```
sudo usermod -aG libvirt $USER
```
## vagrant
En Arch
```
yay -S vagrant
```
vagrant plugin install vagrant-libvirt
vagrant up --provider=libvirt
```

