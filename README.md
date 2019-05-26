# Задание 1 (Установка ОС и настройка LVM, RAID)


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


# Вывод

В этом задании узнал о таких командах, как:

* sfdisk -d /dev/XXXX | sfdisk /dev/YYY
* mdadm --manage /dev/md0 --add /dev/YYY

А так же узнал, как:

* Удалять диск ssd1
* Проверять статус RAID-массива
* Копировать таблицу разделов со старого диска на новый
* Добавлять в рейд массив новый диск
* Выполнять синхронизацию разделов, не входящих в RAID


# Задание 3 (Добавление новых дисков и перенос раздела)

После удаления диска - проверяем состояние

![](screenshots/thirdTask/1.JPG)

Добавляем новый диск

![](screenshots/thirdTask/2.JPG)

Копируем со старого диска на новый

![](screenshots/thirdTask/3.JPG)

Копирование /boot

![](screenshots/thirdTask/4.JPG)

Перемонтировка /boot на живой диск

![](screenshots/thirdTask/5.JPG)

Устанавливаем grub

![](screenshots/thirdTask/6.JPG)

Создание нового RAID-массива с включением только одного нового ssd диска

![](screenshots/thirdTask/7.JPG)

После успешного создания нового физического тома, включив в него ранее созданный RAID массив - выполняем -vgdisplay system -v -pvs -vgs -lvs -a -o+devices

![](screenshots/thirdTask/8.JPG)

![](screenshots/thirdTask/9.JPG)

После перемещения данных со старого диска на новый. Выполняем -vgdisplay system -v -pvs -vgs -lvs -a -o+devices -lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT

![](screenshots/thirdTask/10.JPG)

![](screenshots/thirdTask/11.JPG)

![](screenshots/thirdTask/12.JPG)

Изменение VG, удалив из него диск старого raid

![](screenshots/thirdTask/13.JPG)

В выводе команды pvs у /dev/md0 исчезли VG и Attr. В выводе команды vgs #PV - уменьшилось на 1, VSize, VFree - стали меньше

![](screenshots/thirdTask/14.JPG)

Добавляем новые диски

![](screenshots/thirdTask/15.png)

Скопируем таблицу разделов, установил grub

![](screenshots/thirdTask/16.png)

Изменение размера нового диска (второй раздел)

![](screenshots/thirdTask/17.png)

![](screenshots/thirdTask/18.png)

![](screenshots/thirdTask/19.png)

Перечитывание таблицы разделов

![](screenshots/thirdTask/20.png)

Добавление нового диска

![](screenshots/thirdTask/21.png)

Расширение кол-ва дисков в массиве до 2

![](screenshots/thirdTask/22.png)

Запуск fdisk /dev/sda

![](screenshots/thirdTask/23.png)

Таблица разделов

![](screenshots/thirdTask/24.png)

Расширение raid

![](screenshots/thirdTask/25.png)

--Вывод команды pvs --Расширение размера PV --Вывод команды pvs

![](screenshots/thirdTask/26.png)

Имена новых дисков

![](screenshots/thirdTask/28.png)

Создание raid

![](screenshots/thirdTask/29.png)

Создание нового PV, в этом PV группы с названием data, логического тома с размером всего свободного пространства var_log

![](screenshots/thirdTask/30.png)

Форматирование созданного раздела

![](screenshots/thirdTask/31.png)

Новое хранилище для логов

![](screenshots/thirdTask/32.png)

Синхронизация разделов и меняние их местами

![](screenshots/thirdTask/33.png)

Измнение /etc/fstab

![](screenshots/thirdTask/34.png)

Проверяем

![](screenshots/thirdTask/35.png)
