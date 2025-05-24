+++
date = '2025-05-08T16:42:18+02:00'
draft = false
title = 'Migracion de máquinas en Proxmox sin clusterizar'
+++


Proxmox es un sistema operativo diseñado para hostear máquinas virtuales y contenedores.
Esta solución esta siendo muy apoyada por la comunidad y suele ser la distro de preferencia para
pequeños CPDs y home-labs. En este artículo pasaré a explicar como se pueden migrar máquinas 
virtuales de una instalación de proxmox a otra sin necesidad de clusterizar.

## Pasos a seguir para migrar máquinas en proxmox

Vamos a suponer que tenemos dos ordenadores corriendo proxmox, la ip del primer ordenador es 
**192.168.0.2** y la ip del segundo ordenador es **192.168.0.150**

El primer ordenador tiene dos máquinas virtuales activas, mientras que el segundo no tiene ninguna
la idea es que al final, el segundo ordenador tenga las dos máquinas virtuales corriendo y el segundo
este libre.

## listar las máquinas virtuales

Utilizaremos el comando qm list, para ver las máqunas virtuales que tenemos funcionando, 
y nos fijaremos en que el estado este en stopped

```bash
root@qubata:~# qm list
      VMID NAME                 STATUS     MEM(MB)    BOOTDISK(GB) PID
       100 Daniel-ptp           stopped    2048              32.00 0
       101 juanjo-IDQ-QNET-CS   stopped    4096              20.00 0
```
En casp de que sean contenedores:
```bash
root@quasar:~# pct list
VMID       Status     Lock         Name
101        stopped                 Daniel-llavesNist
103        stopped                 Daniel-llavesNIstCV
```

En caso de que una máquina no este stopped, hay que utilizar el siguiente comando

```bash
qm stop <VMID>
```
siendo VMID el número asociado a la máquina virtual.

En caso de que sean contenedores:
```bash
pct stop <VMID>
```


## Crear un backup de la máquina virtual
 Una vez paradas las máquinas virtuales o los contenedores hay que hacer un backup de las imagenes, esto se hace con 
el comando 

```bash
vzdump <VMID> --compress zstd --dumpdir /var/lib/vz/dump
```
el modo de compresion debe ser zstd y el directorio puede ser cualquiera, pero el directorio donde
proxmox guarda las imagenes es /var/lib/vz. Este proceso se  tiene que hacer con todas las máquinas 
virtuales que se quieran migrar.

En caso de que sean contenedores:

```bash
vzdump <VMID> --dumpdir /var/lib/vz/dump
```

## Transferir las máquinas virtuales
Para transferir las máquinas virtuales, se realizará un scp a la máquina a la que se quieran enviar, en este caso la 192.168.0.150

```bash
scp -r /var/lib/vz/* root@192.168.0.150:/var/lib/vz/
```


## Restaurar las máquina virtuales

Desde la máquina en la que se quieren volver a levantar, hay que correr el siguiente comando con 
todas las máquinas que se quieren volver a levantar

```bash
qmrestore /var/lib/vz/dump/<ARCHIVO-A-TRANSFERIR>.vma.zst <VMID> --storage local-lvm
```

recuerda que los VMID **no se pueden repetir**

En caso de que sean contenedores, es importante que se guarde en local-lvm

```bash
pct restore 106 /var/lib/vz/dump/vzdump-lxc-101-2025_04_23-15_05_22.tar --storage local-lvm
```

## Fallos comunes

- No enciende la máquina, porque el bridge es diferente en la máquina destino
Solución: Editar la conexion de red en el frontend de proxmox en el apartado hardware.

- No funciona el contenedor por no tener la imagen en el local 
Descargarse la imagen que se encuentra en /var/lib/vz/template/cache/ del ordenador con el contenedor
```bash
pveam download local debian-12-standard_12.7-1_amd64.tar.zst
```
