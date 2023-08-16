<!--
## bashrc:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```
-->
## Bluetooth
```
sudo pacman -S bluez bluez-utils pulseaudio-bluetooth && systemctl enable bluetooth.service && systemctl start bluetooth.service
```

# Nvidia setup
### nvidia-settings
```
sudo pacman -S nvidia-settings
```


<!--
### mpv
`/home/bali10050/.config/mpv/mpv.conf`
```
vo=gpu
hwdec=nvdec
profile=gpu-hq
gpu-context=x11
```
-->


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
NVD_BACKEND=direct
```
```
MOZ_ENABLE_WAYLAND=1
```


### ffmpeg
```
./configure --prefix=/usr --disable-debug --disable-static --disable-stripping --enable-lto --enable-fontconfig --enable-gmp --enable-gnutls --enable-gpl --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libdav1d --enable-libdrm --enable-libfreetype --enable-libfribidi --enable-libgsm --enable-libiec61883 --enable-libjack --enable-libjxl --enable-libmfx --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librav1e --enable-librsvg --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libv4l2 --enable-libvidstab --enable-libvmaf --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxcb --enable-libxml2 --enable-libxvid --enable-libzimg --enable-nvdec --enable-nvenc --enable-opengl --enable-shared --enable-version3 --enable-vaapi --disable-x86asm
```

### Firefox
`media.ffmpeg.vaapi.enabled`=`true`


`media.rdd-ffmpeg.enabled`=`true`


`media.av1.enabled`=`false`


`gfx.x11-egl.force-enabled`=`false`


`widget.dmabuf.force-enabled`=`true`

`gfx.webrender.all`=`true`
