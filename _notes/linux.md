Firewall
========
Getting current zone:
firewall-cmd --get-active-zones

Listing open ports:
firewall-cmd --list-all

Open port:
firewall-cmd --zone=public --add-port=32400/tcp --permanent
firewall-cmd --reload

Close port:
firewall-cmd --zone=public --remove-port=10050/tcp
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload

cifs/samba
==========
chmod -R 0755 anonymous/
chown -R nobody:nobody anonymous/
chcon -t samba_share_t anonymous/

ssh
===
Adding authorized public key:
mkdir ~/.ssh
chmod 700 ~/.ssh
vim ~/.ssh/authorized_keys and add key
chmod 600 ~/.ssh/authorized_keys

Server:
sudo apt install openssh-server
sudo vim /etc/ssh/sshd_config "PasswordAuthentication no" "PermitRootLogin no"
sudo systemctl reload sshd

Serial Port
===========
Usually need dialout group to access /dev/ttyX:
sudo usermod -a -G dialout planteen

Shared Libraries
================
Find a symbol in shared libraries:
scanelf -l -s XRRGetCrtcInfo | grep XRRGetCrtcInfo

chmod
=====
Remove execute permissions from files but add to directories
chmod -R -x+X *
-x removes execute for all
+X add execute for all

md5sum
======
Recursively md5sum a folder:
find ./dir -type f -print0 | xargs -0 md5sum > sums.md5
