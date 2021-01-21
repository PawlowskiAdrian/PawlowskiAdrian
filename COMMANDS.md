# Fix LVM encrypted volumes
```
sudo apt-get install cryptsetup
sudo apt-get install lvm2
sudo fdisk -l
sudo lsblk -f /dev/sdb
sudo file -s /dev/sdb3
sudo cryptsetup luksOpen /dev/sdb3
sudo cryptsetup luksOpen /dev/sdb3 encrypted_device
sudo vgdisplay --short
sudo lvs -o lv_name,lv_size -S vg_name=ubuntu-vg
sudo lvchange -ay ubuntu-vg/root
sudo lvchange -ay ubuntu-vg
sudo mkdir /media/repair
sudo mount /dev/ubuntu-vg/root /media/repair/
sudo lvs -S "lv_active=active && vg_name=ubuntu-vg"
sudo lvchange -an ubuntu-vg/root
sudo lvchange -an ubuntu-vg
sudo cryptsetup luksClose encrypted_device
```

# Clean space
```
sudo apt-get autoremove
sudo du -sh /var/cache/apt 
sudo apt-get autoclean
sudo apt-get clean
journalctl --disk-usage
sudo journalctl --vacuum-time=3d
fdupes -d <directory>
```
