# install-nvidia-elementaryos
Install Nvidia Driver for cuda developer


>>>>>     MODO FUENTES y COMPILACION

PRIMERA FASE


1- Primero, descargue el controlador.

    http://www.nvidia.com/download/driverResults.aspx/82252/en-us

2- Para poder instalar su controlador nvidia, debe eliminar su controlador de video anterior con este código en una ventana de terminal:

    sudo apt-get remove nvidia* && sudo apt-get autoremove
    sudo apt-get --purge remove xserver-xorg-video-nouveau

3- Instalar paquetes Básicos para el contralor descargado

    apt-get install dkms build-essential linux-headers-generic

4- Incluir en la lista negra el controlador nouveau editando este archivo con:

    sudo nano /etc/modprobe.d/blacklist-nouveau.conf

blacklist nouveau

blacklist lbm-nouveau

options nouveau modeset=0

alias nouveau off

alias lbm-nouveau off



5- Deshabilite el Kernel nouveau escribiendo los siguientes comandos ( nouveau-kms.confpuede que no exista, está bien):

    echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf

6- Regenerar el kernel initramfs (Asegurate que el initramfs que hace es el mismo con el que arrancas):

    sudo update-initramfs -u
    sudo uname -a

7- Finalmente, reinicie:

    sudo reboot





SEGUNDA FASE

8- sudo service lightdm stop

9- sudo sh NVIDIA-Linux-x86_64*******.run
Accept






>>>>>     MODO KENREL MODULES

1- Instalar modulos necesarios

    apt-get install linux-modules-nvidia-545-6.5.0-27-generic  xserver-xorg-video-nvidia-545 nvidia-utils-545 nvidia-kernel-common-545 nvidia-compute-utils-545

2- Incluir en la lista negra el controlador nouveau editando este archivo con:

    sudo nano /etc/modprobe.d/blacklist-nouveau.conf

blacklist nouveau

blacklist lbm-nouveau

options nouveau modeset=0

alias nouveau off

alias lbm-nouveau off



3- Deshabilite el Kernel nouveau escribiendo los siguientes comandos ( nouveau-kms.confpuede que no exista, está bien):

    echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf

4- Regenerar el kernel initramfs (Asegurate que el initramfs que hace es el mismo con el que arrancas):

    sudo update-initramfs -u
    sudo uname -a

5- Reiniciar

    sudo reboot





