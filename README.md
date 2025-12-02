**Installation**

1. Install plymouth
```bash
# Arch Linux
pacman -S plymouth

# Gentoo
emerge sys-boot/plymouth

# Debian/Ubuntu
apt install apt install plymouth-theme-breeze kde-config-plymouth
```

2. edit /etc/default/grub and add these options
```bash
GRUB_CMDLINE_LINUX_DEFAULT="... quiet splash"
GRUB_GFXPAYLOAD_LINUX=keep
```

3. Clone and use this theme
```bash
sudo git clone https://github.com/maroisa/plymouth-kms.git /usr/share/plymouth/themes/
sudo plymouth-set-default-theme kms-mac-style
```

4. configure initramfs
```bash
# for dracut, it will automatically configured.
# if autodetection fails, edit dracut configuration in /etc/dracut.conf.d/myflags.conf
add_dracutmodules+=" plymouth "

# for mkinitcpio, add HOOKS array in /etc/mkinitcpio.conf
HOOKS=(... plymouth ...)
```

5. Build initramfs
```bash
# dracut
sudo dracut --force

# mkinitcpio
sudo mkinitcpio -p linux
```