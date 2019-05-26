# Лабораторная работа №2 (RAID)

Установка Linux


![](screenshots/firstTask/1.png)

![](screenshots/firstTask/2.png)

![](screenshots/firstTask/3.png)

![](screenshots/firstTask/4.png)

![](screenshots/firstTask/5.png)

![](screenshots/firstTask/6.png)

![](screenshots/firstTask/7.png)

![](screenshots/firstTask/8.png)

![](screenshots/firstTask/9.png)


Установка grub

![](screenshots/firstTask/10.JPG)

![](screenshots/firstTask/11.JPG)

Данные об physical volumes, volume groups, logical volumes с помощью выше использованных команд.

# Вывод

В данном задании выяснилось, как устанавливать OC Linux, настраивать LVM и RAID, и использовать такие команды, как:

* fdisk -l *+pvs,lvs,vgs
* lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
* cat /proc/mdstat
* grub-install /dev/XXX
* dd if=/dev/xxx of=/dev/yyy