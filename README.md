# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Дёмин максим`


### Задание 1
Установите Zabbix Server с веб-интерфейсом.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
Требования к результатам
Прикрепите в файл README.md скриншот авторизации в админке.
Приложите в файл README.md текст использованных команд в GitHub.

### Решение:
1. Установите репозиторий Zabbix
Документация
# wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian13_all.deb
# dpkg -i zabbix-release_latest_7.4+debian13_all.deb
# apt update

maksim@zabbix-debian:~$ cd /tmp
maksim@zabbix-debian:/tmp$ wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian13_all.deb
```
--2026-01-09 09:26:26--  https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian13_all.deb
Resolving repo.zabbix.com (repo.zabbix.com)... 178.128.6.101, 2604:a880:2:d0::2062:d001
Connecting to repo.zabbix.com (repo.zabbix.com)|178.128.6.101|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7144 (7.0K) [application/octet-stream]
Saving to: 'zabbix-release_latest_7.4+debian13_all.deb'

zabbix-release_latest_7.4 100%[==================================>]   6.98K  --.-KB/s    in 0s      

2026-01-09 09:26:27 (73.0 MB/s) - 'zabbix-release_latest_7.4+debian13_all.deb' saved [7144/7144]
```
maksim@zabbix-debian:/tmp$ sudo dpkg -i zabbix-release_latest_7.4+debian13_all.deb
```
Selecting previously unselected package zabbix-release.
(Reading database ... 119317 files and directories currently installed.)
Preparing to unpack zabbix-release_latest_7.4+debian13_all.deb ...
Unpacking zabbix-release (1:7.4-1+debian13) ...
Setting up zabbix-release (1:7.4-1+debian13) ...
```
maksim@zabbix-debian:/tmp$ sudo apt update

<img width="1830" height="836" alt="Screenshot_20260109_174651" src="https://github.com/user-attachments/assets/af68984a-bb24-4b0c-a86d-22172e53a8bf" />
