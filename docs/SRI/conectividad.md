# Conectividad con Internet y red local

## Comprobando interfaces
```
ip link show
```

## Apangando algunas interfaces
```
ip link set dev eth1 down
...
```
## Reinicio de la red
```
sudo systemctl restart networking
```
