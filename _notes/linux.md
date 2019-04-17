Firewall
========
Getting current zone:
```bash
firewall-cmd --get-active-zones
```

Listing open ports:
```bash
firewall-cmd --list-all
```

Open port:
```bash
firewall-cmd --zone=public --add-port=32400/tcp --permanent
firewall-cmd --reload
```

Close port:
```bash
firewall-cmd --zone=public --remove-port=10050/tcp
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload
```

cifs/samba
==========
```bash
chmod -R 0755 anonymous/
chown -R nobody:nobody anonymous/
chcon -t samba_share_t anonymous/
```

ssh
===
Adding authorized public key:
```bash
mkdir ~/.ssh
chmod 700 ~/.ssh
vim ~/.ssh/authorized_keys and add key
chmod 600 ~/.ssh/authorized_keys
```

Server (Debian):
```bash
sudo apt install openssh-server
sudo vim /etc/ssh/sshd_config "PasswordAuthentication no" "PermitRootLogin no"
sudo systemctl reload sshd
```

Server (Red Hat):
```bash
sudo dnf install openssh-server
sudo systemctl start sshd.service
```

Add existing user to existing group
===================================
Usually need `dialout` group to access /dev/ttyX:
```bash
sudo usermod -a -G dialout planteen
```

The group `disk` gives dd access to block storage devices.

To force update without logging in and out:
```bash
exec su -l planteen
```

Shared libraries
================
Find a symbol in shared libraries:
```bash
scanelf -l -s XRRGetCrtcInfo | grep XRRGetCrtcInfo
```

chmod
=====
Remove execute permissions from files but add to directories
```bash
chmod -R -x+X *
```
-x removes execute for all
+X add execute for all

md5sum
======
Recursively md5sum a folder:
```bash
find ./dir -type f -print0 | xargs -0 md5sum > sums.md5
```

Shell buffering
===============
Force buffer flush after each line of output to stdout
```bash
stdbuf -oL ./cmd > log
```

dd over network
===============
To backup an existing Linux system without having to remove the drive, boot
the source computer with a live Linux USB drive. Setup ssh access and then on
machine with destination drive (or file), execute:

```bash
ssh liveuser@192.168.0.108 dd if=/dev/nvme0n1 bs=8192 count=62513451 status=progress | dd of=/dev/nvme0n1
```

(use `lsblk -b` to get exact size in bytes)

NVIDIA drivers
==============
Fedora:
```bash
sudo dnf install fedora-workstation-repositories
sudo dnf config-manager rpmfusion-nonfree-nvidia-driver --set-enabled
sudo dnf install akmod-nvidia acpi
```
