# Setup MacOS

```sh
git clone https://github.com/foxlet/macOS-Simple-KVM.git
cd macOS-Simple-KVM
gemu-img create -f qcow2 MyDisk.qcow2 64G
cat >> basic.sh << EOF
    -drive id=SystemDisk,if=none,file=MyDisk.qcow2 \
    -device ide-hd,bus=sata.4,drive=SystemDisk \
    -nographic -vnc :0 -k fr
```

1. go to disk-utility and format the 64G virtual hard drive

2. come back to the installer and install macos

# FAQ

## My mouse cursor is not at the right position

append this configuration to `basic.sh` script and remove the mouse
cursor (`-device usb-mouse`).

```txt
-usbdevice tablet
```
