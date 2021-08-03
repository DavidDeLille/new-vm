# new-vm
Scripts to install stuff on a clean VM.

------------------------
# VM settings
## Give more resources to VM
## Enable Shared folders
## Choose Network Adapter

# Configure secure password for root and user account
```
passwd
```

# Make /opt writeable
```
sudo su
chmod -R 777 /opt
```

# Settings
## Disable screen saver
## Set timezone
## Set Num Lock on boot
???

# Guest Extentsions
## Check clipboard
## Check dynamic screen size
## Check Shared folders
## Set up Shared folders on boot
```
sudo su
mkdir /mnt/hgfs/
cat << EOF > /etc/rc.local
#!/bin/sh -e
/usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs/ -o subtype=vmhgfs-fuse,allow_other
systemctl restart apparmor.service
exit 0
EOF
chmod +x /etc/rc.local
```

# Symlinks
```
ln -s /mnt/hgfs/Shared/ /s
ln -s /s /root/s
ln -s /usr/share/wordlists/ /w
ln -s /w /root/w
```

# Software
## Update
```
sudo apt-get update
sudo apt-get upgrade -y 
sudo apt-get dist-upgrade -y
```

## Sublime
```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text
```

## Burp
update-alternatives --config java
