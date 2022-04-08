https://www.youtube.com/watch?v=JT0Y0VUP7T4

# install samba
sudo yum install samba samba-client samba-common

# create folder for file share
sudo mkdir -p /srv/samba/secure

# change permissions for share
sudo chmod -R 0770 /srv/samba/secure

# add group for samba
sudo groupadd smbgrp

# add user to group
sudo usermod keycloak -aG smbgrp

# create samba password for user
sudo smbpasswd -a keycloak

# change ownership
sudo chown -R root:smbgrp /srv/samba/secure

# create copy of original samba config
sudo cp /etc/samba/smb.conf /etc/samba/smb.bak

# edit smb.conf
...
[fileshare]
        comment = file share for test
        path = /srv/samba/secure
        valid users = @smbgrp
        public = No
        browseable = Yes
        writable = Yes
        printable = no
        createmask = 0765
...

# check changes
testparm

# restart samba service
sudo systemctl restart smb.service

# restart nmb service
sudo systemctl restart nmb.service

# open firewall for samba
sudo firewall-cmd --permanent --zone=public --add-service=samba

# reload firewall
sudo firewall-cmd --reload

# find ip address
ip a | grep inet
