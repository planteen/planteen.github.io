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
