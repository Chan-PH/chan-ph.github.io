## Nix OS Installation using Terminal

From the terminal:
1. Provide password for the root and nixos account
   - sudo passwd root
   - passwd nixos
2. Check for the pre-assigned IP using ifconfig / ip a
3. Connect using SSH and login with the password you have set earlier
4. Check for your local disk storage space by 
   - lsblk, look for /dev/sda or /dev/sdb whichever match to your intended drive for Nix OS installation
6. Create standard partitions
   a. MBR:
   b. UEFI:
      '# parted /dev/sda -- mklabel gpt
      '# parted /dev/sda -- mkpart primary 2048s 90%
      '# parted /dev/sda -- mkpart primary linux-swap -8GiB 100%
      '# parted /dev/sda -- mkpart ESP fat32 512MiB 512MiB
      '# parted /dev/sda -- set 3 esp on
      
7. Create label for the partition 
   - '# e2label /dev/sda1 root-disk
9. Mount the partition
   - mkdir -p /mnt/root
   - mount /dev/sda1 /mnt/root
11. 
