# Nvidia-Propietary-Arch-Linux
Step by Step Nvidia Propietary Arch

## Nvidia

*Nvidia only, proceed if you own an nvidia card!



**This is my personal conf\installation on nvidia, with modifications i did, ~~and skiping foolishness~~

*Hardware where i got to work nvidia always, with no issues, i can cofirnm is running as `FIRE`:*

* Asus RogStrix G15 with NVIDIA GeForce RTX 3050 Laptop GPU
* Acer Nitro 5 with Nvidia Geforce GTX 1050 (mobile) Laptop GPU

Requirements\Dependencies:

```
linux-headers
base-devel
libva 
```
### Only if you use Wayland, if not skip!
```
qt5-wayland
qt6-wayland
qt5ct
qt6ct
```

Proceed with nvida:

```
libva-nvidia-driver-git
nvidia-dkms
```

Add modules for nvidia:

```
cd /etc/mkinitcpio.conf
sudo neovim mkinitcpio.conf
```
> if mkinitcpio.conf is not there, create it.

Add this into MODULES=() exactly like this, into brackets: 

```
nvidia nvidia_modeset nvidia_uvm nvidia_drm
```

Create the Image:

```
sudo mkinitpcio -P linux
```
#### If mkinitcpio is not found+_?Do>
```
yay -S mkinitcpio

#and then run again

sudo mkinitpcio -P linux

```

IMPORTANT: 
>> If you have `linut-lts`, `linux-zen` use: `sudo mkinitpcio -P linux-lts` , and asap.

Now final Important step:

> If nvidia.conf is not there, make `touch nvidia.conf`  and ready.

```
cd /etc/modprobe.d/nvidia.conf
sudo neovim nvidia.conf
```

Add this:

```
options nvidia-drm modeset=1
```


Thats all!!

### Opcional: if nouveau is giving you Headaches, !!Only!

With

```
blacklist nouveau
```

in

```
/etc/modprobe.d/nouveau.conf
```

regenerat your initramfs with

```
mkinitcpio -p linux
```

Nouveau definitely shouldn't be used.

Chau1

