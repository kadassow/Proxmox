add bind mounts to containers through 
https://www.youtube.com/watch?v=qa2Q7tZVol8&t=9s

add NAS mounts to unprivileged lxc
https://forum.proxmox.com/threads/tutorial-unprivileged-lxcs-mount-cifs-shares.101795/
https://forum.proxmox.com/threads/tutorial-mounting-nfs-share-to-an-unprivileged-lxc.138506/

on lxc - 
groupadd -g 10000 lxc_shares
sudo useradd keith
usermod -aG lxc_shares keith

on pve host
mkdir /mnt/lxc_shares/pictures
Code:
{ echo '' ; echo '# Mount CIFS share on demand with rwx permissions for use in LXCs (manually added)' ; echo '//192.168.69.150/data/media/pictures /mnt/lxc_shares/pictures cifs _netdev,x-systemd.automount,noatime,uid=100000,gid=110000,dir_mode=0770,file_mode=0770,user=keith,pass=123abc 0 0' ; } | tee -a /etc/fstab
mount /mnt/lxc_shares/pictures
{ echo 'mp0: /mnt/lxc_shares/pictures/,mp=/mnt/pictures' ; } | tee -a /etc/pve/lxc/232.conf



/etc/pve/lxc/xxx.conf
mp<id>: <hostpath>,mp=<containerPath>
mp0: /mnt/pve/bigdrive,mp=/mnt/pve/bigdrive


https://trash-guides.info/

resizing VM disks
https://arcrow.com/how-resize-proxmox-vms-lvm-disk/

check container ip
docker exec -it <containerName> /bin/bash -c "curl ipinfo.io/$(curl ifconfig.me)"
curl ipinfo.io/$(curl ifconfig.me)
