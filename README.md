# DVEC

## Настройка sudo
Для настройки необходимо польхзователя юоавить в группу `wheel`
```
# usermod -a -G wheel n_lyalav
```
Применить настройки группы уже в сессии пользователя
```
$ newgrp wheel
```

## Подключение общих папок
Диски подключаются с правами авторизовавшегося пользователя. Работает при входе в графичечкую оболочку или консоль. Точка подключения `mountpoint` должны существовать. Папка прописанные в параметрах `mountpoint="/media/%(USER)/alpine-obmen"` будут созданы. Подключенные ресурсы отображаются на рабочем столе 
![alt text](./pam_mount.png)
Конфиг pam_mount `/etc/security/pam_mount.conf.xml`
Подключение общего диска с шары сервера Windows 2003, ключевые моменты `sec=krb5`, `vers=1.0` 
```
<volume fstype="cifs" server="alpine.prim.dvec.ru" path="Обмен" mountpoint="/media/%(USER)/alpine-obmen" options="user=%(USER),rw,setuids,perm,soft,sec=krb5,cruid=%(USERUID),iocharset=utf8,vers=1.0"/>
```
Для подключения шары Winodws 2008 сервер
```
<volume fstype="cifs" server="nhk-erits-srv.prim.dvec.ru" path="Обмен" mountpoint="/media/%(USER)/erits-obmen" options="user=%(USER),rw,setuids,perm,soft,sec=krb5i,cruid=%(USERUID),iocharset=utf8"/>
<volume fstype="cifs" server="nhk-erits-srv.prim.dvec.ru" path="Ериц" mountpoint="/media/%(USER)/erits" options="user=%(USER),rw,setuids,perm,soft,sec=krb5i,cruid=%(USERUID),iocharset=utf8"/>
```
