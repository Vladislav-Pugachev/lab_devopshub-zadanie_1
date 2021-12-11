>1. Cкачивавание образа сервера Ubuntu
```buildoutcfg
https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64.img
```
>2. При развертывании образа для доступа по паролю к серверу создал начальный скрипт:
```buildoutcfg
#cloud-config
password: test
```
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/change_passwd.png)
>3. Установка GUI для доступа к horizon
```buildoutcfg
root@ubntu:~# apt install xfce4
```
>4. Создание пользователя stack
```buildoutcfg
root@stack:~# useradd -s /bin/bash -d /opt/stack -m stack
root@stack:~# echo "stack ALL=(ALL) NOPASSWD: ALL" | tee /etc/sudoers.d/stack
```
>5. Скачивание архива в домашнюю директорию пользователя stack
```buildoutcfg
stack@stack:~$ git clone https://opendev.org/openstack/devstack -b stable/wallaby
```
>6. Создание кофигурационнго файла
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/local_conf.png)

>7. Запуск скрипта
```buildoutcfg
stack@stack:~/devstack$  ./stack.sh 
```
>8. По завершению установки, проверка доступности horizon

![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/horizon.png)

>9. скачивание образа для инстанса
```buildoutcfg
https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64.img
```
>10. Создание образа 
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/image_for_instance.png)

>11. Создание instance с ключем для доступа по ssh
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/instance.png)

> 12. Проверка доступа к инстанс через консоль
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/instance_console.png)

> 13. Создание файла на основном серевере с приватным ключем для доступа по ssh к  instance в директории .shh/, изменение прав для данного файла
``` buildoutcfg
nano rsa_key
chmod 600 id_rsa
```
> 14. Для связности с созданным instane, создал маршрутизатор
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/router.png)
>15. Для доступа к openstack через CLI скачал файлик Open-Stack RC файл и добавил в окружение данные из него:
```buildoutcfg
ubuntu@stack:~/Downloads$source admin-openrc.sh
```
>16. Доступ к instance осуществляется через его пространсво имен.

![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/namespace.png)

>17. Проверка доступа по ssh
![скриншот](https://github.com/Vladislav-Pugachev/lab_devopshub-zadanie_1/blob/main/ssh_instance.png) 
