# install-nvidia-elementaryos
Install Nvidia Driver for cuda developer

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

6- Regenerar el kernel initramfs:

    sudo update-initramfs -u

7- Finalmente, reinicie:

    sudo reboot

