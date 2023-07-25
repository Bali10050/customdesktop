## bashrc:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```
## Bluetooth
```
sudo pacman -S blueman
```
```
sudo pacman -S bluez
```
```
sudo pacman -S bluez-utils
```
```
systemctl enable bluetooth.service
```
```
systemctl start bluetooth.service
```


# Nvidia setup
### mpv
`/home/bali10050/.config/mpv/mpv.conf`
```
vo=gpu
hwdec=nvdec
profile=gpu-hq
gpu-context=x11
```

### yay
```
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

## libva
### Install
```
yay -S libva-nvidia-driver
```
### Kernel parameter
`/etc/default/grub`

Add `nvidia-drm.modeset=1` to `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
```

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

### Environment
`/etc/environment`
```
MOZ_DISABLE_RDD_SANDBOX=1
LIBVA_DRIVER_NAME=nvidia
__EGL_VENDOR_LIBRARY_FILENAMES=/usr/share/glvnd/egl_vendor.d/10_nvidia.json
```


