partition:
sudo fdisk /dev/sdb n p 2 0 1-4 p ou entrer +6G w pour garder
![Capture d'écran 2025-01-28 114034](https://github.com/user-attachments/assets/0e03e1d5-4ada-4817-b3ad-06d02f911dae)

partition de 6 Go de type ext4 nommée "DATA"
sudo mkfs.ext4 /dev/sdb2 sudo mkfs.ext4 -L DATA /dev/sdb2

partition avec le reste du disque de type swap nommé "SWAP"
fdisk /dev/sdb n t L p 82 w

mkswap /dev/sdb3 swapon/dev/sdb3

Montage automatique
![Capture d'écran 2025-01-28 114044](https://github.com/user-attachments/assets/11ced885-e798-4c69-b4a3-67dfb957c613)

Récupérer l'UUID blkid /dev/sdb2
UUID=b56cb481-a6aa-437d-9bb6-be72412ada3c /mnt/DATA ext4 par défaut 0 2 UUID=fd5ec5e9-b8c7-4333-a498-d944ccb43f98 aucun échange sw 0 0 
nano etc/fstab/ ajouter dans la dernière ligne

UUID=b56cb481-a6aa-437d-9bb6-be72412ada3c /mnt/DATA ext4 par défaut 0 2 UUID=fd5ec5e9-b8c7-4333-a498-d944ccb43f98 aucun swap sw 0 0 mkdir -p /mnt/DATA mount /mnt/DATA VÉRIFICATEUR : 
Lsblk -f
![Capture d'écran 2025-01-28 114052](https://github.com/user-attachments/assets/aa539aeb-5727-4b96-982c-74fd8dfff407)

