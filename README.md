# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Дёмин Максим`


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
```
 wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian13_all.deb
 dpkg -i zabbix-release_latest_7.4+debian13_all.deb
 apt update
```
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

2. установка apache2 php

maksim@zabbix-debian:/tmp$ sudo apt -y install apache2 php libapache2-mod-php \
  php-pgsql php-gd php-xml php-bcmath php-mbstring php-ldap php-curl
```
Installing:                     
  apache2             php         php-curl  php-ldap      php-pgsql
  libapache2-mod-php  php-bcmath  php-gd    php-mbstring  php-xml

Installing dependencies:
  apache2-bin            libaprutil1-dbd-sqlite3  php-common     php8.4-curl      php8.4-pgsql
  apache2-data           libaprutil1-ldap         php8.4         php8.4-gd        php8.4-readline
  apache2-utils          libaprutil1t64           php8.4-bcmath  php8.4-ldap      php8.4-xml
  libapache2-mod-php8.4  liblua5.4-0              php8.4-cli     php8.4-mbstring
  libapr1t64             libonig5                 php8.4-common  php8.4-opcache

Suggested packages:
  apache2-doc  apache2-suexec-pristine  | apache2-suexec-custom  ufw  php-pear

Summary:
  Upgrading: 0, Installing: 33, Removing: 0, Not Upgrading: 0
  Download size: 8741 kB
  Space needed: 37.6 MB / 3714 MB available

Get:1 http://security.debian.org/debian-security trixie-security/main amd64 php8.4-common amd64 8.4.16-1~deb13u1 [767 kB]
Get:2 http://ftp.ru.debian.org/debian trixie/main amd64 libapr1t64 amd64 1.7.5-1 [104 kB]
Get:3 http://ftp.ru.debian.org/debian trixie/main amd64 libaprutil1t64 amd64 1.6.3-3+b1 [89.4 kB]
Get:4 http://ftp.ru.debian.org/debian trixie/main amd64 libaprutil1-dbd-sqlite3 amd64 1.6.3-3+b1 [14.2 kB]
Get:5 http://ftp.ru.debian.org/debian trixie/main amd64 libaprutil1-ldap amd64 1.6.3-3+b1 [12.3 kB]
Get:6 http://ftp.ru.debian.org/debian trixie/main amd64 liblua5.4-0 amd64 5.4.7-1+b2 [147 kB]
Get:7 http://ftp.ru.debian.org/debian trixie/main amd64 apache2-bin amd64 2.4.65-2 [1405 kB]
Get:8 http://ftp.ru.debian.org/debian trixie/main amd64 apache2-data all 2.4.65-2 [160 kB]
Get:9 http://ftp.ru.debian.org/debian trixie/main amd64 apache2-utils amd64 2.4.65-2 [215 kB]
Get:10 http://ftp.ru.debian.org/debian trixie/main amd64 apache2 amd64 2.4.65-2 [224 kB]
Get:11 http://ftp.ru.debian.org/debian trixie/main amd64 php-common all 2:96 [13.3 kB]
Get:12 http://ftp.ru.debian.org/debian trixie/main amd64 libapache2-mod-php all 2:8.4+96 [4068 B]
Get:13 http://ftp.ru.debian.org/debian trixie/main amd64 libonig5 amd64 6.9.9-1+b1 [189 kB]
Get:14 http://ftp.ru.debian.org/debian trixie/main amd64 php all 2:8.4+96 [3936 B]
Get:15 http://ftp.ru.debian.org/debian trixie/main amd64 php-bcmath all 2:8.4+96 [3968 B]
Get:16 http://ftp.ru.debian.org/debian trixie/main amd64 php-curl all 2:8.4+96 [3960 B]
Get:17 http://ftp.ru.debian.org/debian trixie/main amd64 php-gd all 2:8.4+96 [3960 B]
```
<img width="1920" height="1080" alt="Screenshot_20260109_174839" src="https://github.com/user-attachments/assets/3ea05d56-bad1-4446-b0ee-b8509bdeece7" />

3. Установите Zabbix сервер, веб-интерфейс и агент
 apt install zabbix-server-pgsql zabbix-frontend-php php8.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

maksim@zabbix-debian:/tmp$ sudo apt -y install zabbix-server-pgsql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
Installing:                     
  zabbix-agent  zabbix-apache-conf  zabbix-frontend-php  zabbix-server-pgsql  zabbix-sql-scripts

Installing dependencies:
  fping      libevent-core-2.1-7t64   libevent-pthreads-2.1-7t64  libodbc2    libopenipmi0t64
  libcares2  libevent-extra-2.1-7t64  libmodbus5                  libodbccr2  snmpd

Suggested packages:
  odbc-postgresql  tdsodbc  snmptrapd  zabbix-nginx-conf

Summary:
  Upgrading: 0, Installing: 15, Removing: 0, Not Upgrading: 0
  Download size: 23.4 MB
  Space needed: 110 MB / 3674 MB available

Get:1 http://ftp.ru.debian.org/debian trixie/main amd64 snmpd amd64 5.9.4+dfsg-2 [57.8 kB]
Get:2 http://ftp.ru.debian.org/debian trixie/main amd64 libevent-core-2.1-7t64 amd64 2.1.12-stable-10+b1 [132 kB]
Get:3 http://ftp.ru.debian.org/debian trixie/main amd64 libevent-extra-2.1-7t64 amd64 2.1.12-stable-10+b1 [108 kB]
Get:4 http://ftp.ru.debian.org/debian trixie/main amd64 libevent-pthreads-2.1-7t64 amd64 2.1.12-stable-10+b1 [54.3 kB]
Get:5 http://ftp.ru.debian.org/debian trixie/main amd64 libodbc2 amd64 2.3.12-2 [151 kB] 
```
<img width="1920" height="1080" alt="Screenshot_20260109_174918" src="https://github.com/user-attachments/assets/f3403df6-4666-4e5d-b975-b70b04bfec9d" />

4. Создайте базу данных
Документация
Установите и запустите сервер базы данных.

Выполните следующие комманды на хосте, где будет распологаться база данных.

 sudo -u postgres createuser --pwprompt zabbix
 sudo -u postgres createdb -O zabbix zabbix

maksim@zabbix-debian:/tmp$ sudo -u postgres createuser --pwprompt zabbix
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = (unset),
	LC_NUMERIC = "ru_RU.UTF-8",
	LC_COLLATE = (unset),
	LC_TIME = "ru_RU.UTF-8",
	LC_MESSAGES = (unset),
	LC_MONETARY = "ru_RU.UTF-8",
	LC_ADDRESS = "ru_RU.UTF-8",
	LC_IDENTIFICATION = "ru_RU.UTF-8",
	LC_MEASUREMENT = "ru_RU.UTF-8",
	LC_PAPER = "ru_RU.UTF-8",
	LC_TELEPHONE = "ru_RU.UTF-8",
	LC_NAME = "ru_RU.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
Enter password for new role: 
Enter it again: 
```
maksim@zabbix-debian:/tmp$ sudo -u postgres createdb -O zabbix -E Unicode -T template0 zabbix
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = (unset),
	LC_NUMERIC = "ru_RU.UTF-8",
	LC_COLLATE = (unset),
	LC_TIME = "ru_RU.UTF-8",
	LC_MESSAGES = (unset),
	LC_MONETARY = "ru_RU.UTF-8",
	LC_ADDRESS = "ru_RU.UTF-8",
	LC_IDENTIFICATION = "ru_RU.UTF-8",
	LC_MEASUREMENT = "ru_RU.UTF-8",
	LC_PAPER = "ru_RU.UTF-8",
	LC_TELEPHONE = "ru_RU.UTF-8",
	LC_NAME = "ru_RU.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
```
<img width="1920" height="1080" alt="Screenshot_20260109_175010" src="https://github.com/user-attachments/assets/efb676b5-9bee-4541-86e0-06a9762383dc" />

На хосте Zabbix сервера импортируйте начальную схему и данные. Вам будет предложено ввести недавно созданный пароль.

 zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

maksim@zabbix-debian:/tmp$ SQL_GZ="$(dpkg -L zabbix-sql-scripts | grep -E 'postgresql/server\.sql\.gz$' | head -n1)"
maksim@zabbix-debian:/tmp$ echo "$SQL_GZ"
/usr/share/zabbix/sql-scripts/postgresql/server.sql.gz
maksim@zabbix-debian:/tmp$ zcat "$SQL_GZ" | sudo -u zabbix psql zabbix
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = (unset),
	LC_NUMERIC = "ru_RU.UTF-8",
	LC_COLLATE = (unset),
	LC_TIME = "ru_RU.UTF-8",
	LC_MESSAGES = (unset),
	LC_MONETARY = "ru_RU.UTF-8",
	LC_ADDRESS = "ru_RU.UTF-8",
	LC_IDENTIFICATION = "ru_RU.UTF-8",
	LC_MEASUREMENT = "ru_RU.UTF-8",
	LC_PAPER = "ru_RU.UTF-8",
	LC_TELEPHONE = "ru_RU.UTF-8",
	LC_NAME = "ru_RU.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
CREATE TABLE
CREATE INDEX
CREATE TABLE
CREATE INDEX
CREATE TABLE
CREATE INDEX
CREATE INDEX
CREATE INDEX
CREATE TABLE
CREATE INDEX
CREATE INDEX
CREATE TABLE
CREATE INDEX
CREATE TABLE
CREATE INDEX
CREATE INDEX
CREATE INDEX
CREATE INDEX
CREATE INDEX
CREATE INDEX
...
INSERT 0 23927
INSERT 0 1
INSERT 0 995
INSERT 0 1277
INSERT 0 180
INSERT 0 180
INSERT 0 199
INSERT 0 17
INSERT 0 168
INSERT 0 6
INSERT 0 13
INSERT 0 15
INSERT 0 1490
INSERT 0 28996
INSERT 0 1
INSERT 0 358
INSERT 0 1
INSERT 0 592
INSERT 0 2728
INSERT 0 16982
DELETE 100173
COMMIT
```
<img width="1920" height="1080" alt="Screenshot_20260109_174355" src="https://github.com/user-attachments/assets/6c4b5f98-3e40-42c4-bbd9-72a80e6c146b" />

5. Настройте базу данных для Zabbix сервера
Отредактируйте файл /etc/zabbix/zabbix_server.conf

DBPassword=password

maksim@zabbix-debian:/tmp$ sudo nano /etc/zabbix/zabbix_server.conf
```
### Option: DBPassword
#       Database password.
#       Comment this line if no password is used.
#
# Mandatory: no
# Default:
DBPassword=XXXXXXX
```
<img width="1920" height="1080" alt="Screenshot_20260109_175243" src="https://github.com/user-attachments/assets/e3307a7a-8019-48a9-9fec-2fe23659804e" />


maksim@zabbix-debian:/tmp$ sudo nano /etc/zabbix/apache.conf
```
php_value date.timezone Europe/Moscow
```
6. Запустите процессы Zabbix сервера и агента
Запустите процессы Zabbix сервера и агента и настройте их запуск при загрузке ОС.

 systemctl restart zabbix-server zabbix-agent apache2
 systemctl enable zabbix-server zabbix-agent apache2

maksim@zabbix-debian:/tmp$ sudo systemctl enable --now zabbix-server zabbix-agent apache2
```
Synchronizing state of zabbix-server.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable zabbix-server
```
<img width="1920" height="1080" alt="Screenshot_20260109_175356" src="https://github.com/user-attachments/assets/f3a8e816-346f-46ba-a60b-98f2585b06ca" />

6. http://192.168.0.2/zabbix
<img width="1919" height="1079" alt="Screenshot_20260109_173648" src="https://github.com/user-attachments/assets/5d71d980-c292-446a-a8ca-e398753de8f9" />
<img width="1919" height="1079" alt="Screenshot_20260109_173719" src="https://github.com/user-attachments/assets/0602082d-95b3-4a05-897a-5a11f57e31c0" />
<img width="1919" height="1079" alt="Screenshot_20260109_173828" src="https://github.com/user-attachments/assets/3646e4f2-506a-40cb-9daf-0803013dfed3" />
<img width="1919" height="1079" alt="Screenshot_20260109_173904" src="https://github.com/user-attachments/assets/9d656108-4129-4b0e-b5e1-87453ae0115d" />
<img width="1919" height="1079" alt="Screenshot_20260109_173919" src="https://github.com/user-attachments/assets/c6457387-5363-4ca5-8efa-01b25881b454" />
<img width="1919" height="1079" alt="Screenshot_20260109_173940" src="https://github.com/user-attachments/assets/64528158-17cc-4e83-a084-5ef86bf7bd5a" />
<img width="1919" height="1079" alt="Screenshot_20260109_174004" src="https://github.com/user-attachments/assets/927448b1-2ab3-4936-92e2-8049300ccad8" />
<img width="1919" height="1079" alt="Screenshot_20260109_174018" src="https://github.com/user-attachments/assets/ab7b902b-6cbf-4705-b1c0-91a6f4875526" />

### Задание 2
Установите Zabbix Agent на два хоста.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.
Требования к результатам
Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Приложите в файл README.md текст использованных команд в GitHub

### Решение:
