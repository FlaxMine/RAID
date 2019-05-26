﻿# Задание 1 (Установка ОС и настройка LVM, RAID)


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

Данные об physical volumes, volume groups, logical volumes выводятся с помощью выше использованных команд.

# Вывод

В данном задании выяснилось, как устанавливать OC Linux, настраивать LVM и RAID, и использовать такие команды, как:

* fdisk -l *+pvs,lvs,vgs
* lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
* cat /proc/mdstat
* grub-install /dev/XXX
* dd if=/dev/xxx of=/dev/yyy

# Задание 2 (Эмуляция отказа  одного из дисков)

После удаления и добавления нового - проверяем, появился ли он в системе или нет с помощью команды fdisk -l

![](screenshots/secondTask/1.png)

С помощью команды sfdisk -d /dev/XXXX | sfdisk /dev/YYY копируем таблицы разделов на новый диск

![](screenshots/secondTask/2.JPG)

mdadm --manage /dev/md0 --add /dev/YYY - добавление в рейд массив нового диска

![](screenshots/secondTask/3.JPG)

Результат cat /proc/mdstat/

![](screenshots/secondTask/4.JPG)

Синхронизация разделов

![](screenshots/secondTask/5.JPG)

Устанавливаем grub на новый диск

![](screenshots/secondTask/7.png)

Проверяем, что все отлично работает!

![](screenshots/secondTask/6.png)


