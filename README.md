add bind mounts to containers through 
https://www.youtube.com/watch?v=qa2Q7tZVol8&t=9s
/etc/pve/lxc/xxx.conf
mp<id>: <hostpath>,mp=<containerPath>
mp0: /mnt/pve/bigdrive,mp=/mnt/pve/bigdrive
