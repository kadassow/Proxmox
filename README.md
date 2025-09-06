add bind mounts to containers through 
https://www.youtube.com/watch?v=qa2Q7tZVol8&t=9s

/etc/pve/lxc/xxx.conf
mp<id>: <hostpath>,mp=<containerPath>
mp0: /mnt/pve/bigdrive,mp=/mnt/pve/bigdrive


https://trash-guides.info/

resizing VM disks
https://arcrow.com/how-resize-proxmox-vms-lvm-disk/

check container ip
docker exec -it <containerName> /bin/bash -c "curl ipinfo.io/$(curl ifconfig.me)"
curl ipinfo.io/$(curl ifconfig.me)
