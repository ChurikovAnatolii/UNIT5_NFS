## UNIT5_NFS

### 1. vagrant up должен поднимать 2 виртуалки: сервер и клиент

-***Создан [Vagrantfile](https://github.com/ChurikovAnatolii/UNIT5_NFS/blob/main/Vagrantfile), который поднимает 2 хоста: сервер и клиент c bridge- интерфейсами***.

### 2. На сервер должна быть расшарена директория и в шаре должна быть папка upload с правами на запись

-***Установим nfs-окружение на сервере, создадим директорию и расшарим ее***
> yum install nfs-utils -y  
> systemctl start nfs-server  
> systemctl enable  nfs-server -**Добавим старт при запуске**  
> mkdir mnt/share/upload  
> echo 'mnt/share/upload/ *(rw,no_root_squash)' >> etc/exports

> exportfs -s 
>> /mnt/share/upload *(sync,wdelay,hide,no_subtree_check,sec=sys,rw,secure,no_root_squash,no_all_squash)

> showmount --exports -**Проверим, что экспортируется**  
>> Export list for server:  
>> /mnt/share/upload *  


### 3. На клиента она должна автоматически монтироваться при старте (fstab или autofs)

-***Установим nfs-окружение на клиенте
> yum install nfs-utils -y  
> systemctl start nfs-server
> mkdir mnt/share/upload 
> systemctl enable  nfs-server -**Добавим старт при запуске**   
> showmount --exports 192.168.1.92 -**Проверим, что экспортируется на сервере**    
>> Export list for 192.168.1.92:    
>> /mnt/share/upload *    

> 

