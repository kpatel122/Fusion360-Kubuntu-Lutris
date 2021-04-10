# Fusion 360 on Kubuntu 20.0.4 with AMD R9 M375 (Lenovo Lptop)
1) Install Lutris
2) Install fusion from Lutris
3) Switch Wine to to Lutris 4.20- lutris-lol-4.20-x86_64 (other versions may also work, best to experiment)
4) Enable ACO shader compiler in Lutris 
5) Install vulkan (the site below has instructions for various OS and graphics cards)

https://linuxconfig.org/install-and-test-vulkan-on-linux#h4-1-debian
from the site above for ubuntu & AMD
```sh
$ sudo add-apt-repository ppa:oibaf/graphics-drivers
$ sudo apt update
$ sudo apt upgrade
$ sudi apt install libvulkan1 mesa-vulkan-drivers vulkan-utils
```
Check vulkan install
```sh
6 ) vulkaninfo | less
```
7) blacklist default radeon driver (R9 200/300 series )
https://github.com/ValveSoftware/Proton/wiki/Requirements#enable-vulkan-on-radeon-r9-200300-series

From the site above
```sh
echo "blacklist radeon" | sudo tee --append /etc/modprobe.d/blacklist.conf
echo "options amdgpu si_support=1 cik_support=1" | sudo tee --append /etc/modprobe.d/amdgpu.conf
sudo update-initramfs -u
```
8) run Fusion 360 and switch graphics renderer to OpenGL

9) Remove DirectX libs from Wine

10) Install winetricks packages

corefonts
vcrun2017
msxml4
dxvk

```sh
env WINE=/home/$USER/.local/share/lutris/runners/wine/lutris-lol-4.20-x86_64/bin/wine winetricks corefonts
env WINE=/home/$USER/.local/share/lutris/runners/wine/lutris-lol-4.20-x86_64/bin/wine winetricks vcrun2017
env WINE=/home/$USER/.local/share/lutris/runners/wine/lutris-lol-4.20-x86_64/bin/wine winetricks msxml4
env WINE=/home/$USER/.local/share/lutris/runners/wine/lutris-lol-4.20-x86_64/bin/wine dxvk
```

11) make sure you have DRI_PRIME set to use dedicated graphics & run Fusion 360 

https://www.youtube.com/watch?v=7-ckiKQotNw


$:  DRI_PRIME=1 lutris %U



