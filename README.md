# KEST2LG05DU_Lokaverkefni

https://www.howtoforge.com/perfect-server-debian-10-buster-apache-bind-dovecot-ispconfig-3-1/
```
su -
nano /etc/network/interfaces
```
![interfaces](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/interfaces.PNG?raw=true)

```
nano /etc/hosts
```
![hosts](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/hosts.PNG?raw=true)

```
nano /etc/hostname
```
![hostname](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/hostname.PNG?raw=true)

```
adduser --force-badname AleRag
```
![adduser](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/adduser.PNG?raw=true)

```
ls -l /home
```
![homedir](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/homedir.PNG?raw=true)

```
sudo groupadd IT
sudo groupadd Management
sudo groupadd Accounting
sudo groupadd Manufacturing
```
![groupadd](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/groupadd.PNG?raw=true)

```
usermod -a -G IT AleRag
usermod -a -G IT AndHau
usermod -a -G Management GudSte
usermod -a -G Management HalJon
usermod -a -G Management HarHja
usermod -a -G Accounting HraAra
usermod -a -G Accounting IngGud
usermod -a -G Manufacturing IsaLei
usermod -a -G Manufacturing JohKri
usermod -a -G Manufacturing JohHaf
usermod -a -G Manufacturing KriSva
usermod -a -G Manufacturing LarGun
usermod -a -G Manufacturing LinMag
usermod -a -G Manufacturing RudBjo
usermod -a -G Manufacturing SigSte
usermod -a -G Manufacturing SigJen
```
![usermod](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/usermod.PNG?raw=true)

```
sudo apt install samba

chgrp Management /opt/Management
chmod -R 770 /opt/Management

smbpasswd -a AleRag
smbpasswd -e AleRag

nano /etc/samba/smb.conf
```
![samba](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/smbcnf.PNG?raw=true)
![samba2](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/smbcnf2.PNG?raw=true)
```
systemctl restart smbd

nano /etc/ssh/sshd_config
```
![sshd](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/sshd.PNG?raw=true)
```
systemctl restart sshd

apt-get -y install apache2 apache2-doc apache2-utils libapache2-mod-php php7.3 php7.3-common php7.3-gd php7.3-mysql php7.3-imap php7.3-cli php7.3-cgi libapache2-mod-fcgid apache2-suexec-pristine php-pear mcrypt  imagemagick libruby libapache2-mod-python php7.3-curl php7.3-intl php7.3-pspell php7.3-recode php7.3-sqlite3 php7.3-tidy php7.3-xmlrpc php7.3-xsl memcached php-memcache php-imagick php-gettext php7.3-zip php7.3-mbstring memcached libapache2-mod-passenger php7.3-soap php7.3-fpm php7.3-opcache php-apcu

a2enmod suexec rewrite ssl actions include dav_fs dav auth_digest cgi headers actions proxy_fcgi alias

nano /etc/apache2/conf-available/httpoxy.conf
```
![httpoxy](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/httpoxy.PNG?raw=true)

```
a2enconf httpoxy
systemctl restart apache2

cd /usr/local/bin
wget https://dl.eff.org/certbot-auto
chmod a+x certbot-auto
./certbot-auto --install-only

apt-get install mailman
newlist mailman

nano /etc/aliases
```
![aliases](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/aliases.PNG?raw=true)

```
newaliases
systemctl restart postfix
ln -s /etc/mailman/apache.conf /etc/apache2/conf-enabled/mailman.conf
systemctl restart apache2
systemctl restart mailman

apt-get install pure-ftpd-common pure-ftpd-mysql quota quotatool
openssl dhparam -out /etc/ssl/private/pure-ftpd-dhparams.pem 2048
nano /etc/default/pure-ftpd-common

VIRTUALCHROOT=true

echo 1 > /etc/pure-ftpd/conf/TLS
mkdir -p /etc/ssl/private/
openssl req -x509 -nodes -days 7300 -newkey rsa:2048 -keyout /etc/ssl/private/pure-ftpd.pem -out /etc/ssl/private/pure-ftpd.pem
chmod 600 /etc/ssl/private/pure-ftpd.pem
systemctl restart pure-ftpd-mysql

nano /etc/fstab
```
![fstab](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/fstab.PNG?raw=true)

```
mount -o remount /
quotacheck -avugm
quotaon -avug

apt-get install bind9 dnsutils
apt-get install haveged

apt-get install webalizer awstats geoip-database libclass-dbi-mysql-perl libtimedate-perl
nano /etc/cron.d/awstats
comment out everything

apt-get install build-essential autoconf automake libtool flex bison debhelper binutils

cd /tmp
wget http://olivier.sessink.nl/jailkit/jailkit-2.20.tar.gz
tar xvfz jailkit-2.20.tar.gz
cd jailkit-2.20
echo 5 > debian/compat
./debian/rules binary

cd ..
dpkg -i jailkit_2.20-1_*.deb
rm -rf jailkit-2.20*

apt-get install fail2ban
nano /etc/fail2ban/jail.local
```
![jail](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/jaillocal.PNG?raw=true)

```
systemctl restart fail2ban
apt-get install ufw

mkdir /usr/share/phpmyadmin
mkdir /etc/phpmyadmin
mkdir -p /var/lib/phpmyadmin/tmp
chown -R www-data:www-data /var/lib/phpmyadmin
touch /etc/phpmyadmin/htpasswd.setup

cd /tmp
wget https://files.phpmyadmin.net/phpMyAdmin/4.9.0.1/phpMyAdmin-4.9.0.1-all-languages.tar.gz

tar xfz phpMyAdmin-4.9.0.1-all-languages.tar.gz
mv phpMyAdmin-4.9.0.1-all-languages/* /usr/share/phpmyadmin/
rm phpMyAdmin-4.9.0.1-all-languages.tar.gz
rm -rf phpMyAdmin-4.9.0.1-all-languages

cp /usr/share/phpmyadmin/config.sample.inc.php  /usr/share/phpmyadmin/config.inc.php
nano /usr/share/phpmyadmin/config.inc.php
```
![secret](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/blowfish.PNG?raw=true)

```
nano /etc/apache2/conf-available/phpmyadmin.conf
```
![](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/phpmyadmin%20apache2.PNG?raw=true)

```
a2enconf phpmyadmin
systemctl restart apache2

mysql -u root -p
```
```sql
CREATE USER 'pma'@'localhost' IDENTIFIED BY '123';
GRANT ALL PRIVILEGES ON phpmyadmin.* TO 'pma'@'localhost' IDENTIFIED BY '123' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT;
```

```
mysql -u root -p phpmyadmin < /usr/share/phpmyadmin/sql/create_tables.sql

nano /usr/share/phpmyadmin/config.inc.php

/* User used to manipulate with storage */
$cfg['Servers'][$i]['controlhost'] = 'localhost';
$cfg['Servers'][$i]['controlport'] = '';
$cfg['Servers'][$i]['controluser'] = 'pma';
$cfg['Servers'][$i]['controlpass'] = '123';

/* Storage database and tables */
$cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
$cfg['Servers'][$i]['bookmarktable'] = 'pma__bookmark';
$cfg['Servers'][$i]['relation'] = 'pma__relation';
$cfg['Servers'][$i]['table_info'] = 'pma__table_info';
$cfg['Servers'][$i]['table_coords'] = 'pma__table_coords';
$cfg['Servers'][$i]['pdf_pages'] = 'pma__pdf_pages';
$cfg['Servers'][$i]['column_info'] = 'pma__column_info';
$cfg['Servers'][$i]['history'] = 'pma__history';
$cfg['Servers'][$i]['table_uiprefs'] = 'pma__table_uiprefs';
$cfg['Servers'][$i]['tracking'] = 'pma__tracking';
$cfg['Servers'][$i]['userconfig'] = 'pma__userconfig';
$cfg['Servers'][$i]['recent'] = 'pma__recent';
$cfg['Servers'][$i]['favorite'] = 'pma__favorite';
$cfg['Servers'][$i]['users'] = 'pma__users';
$cfg['Servers'][$i]['usergroups'] = 'pma__usergroups';
$cfg['Servers'][$i]['navigationhiding'] = 'pma__navigationhiding';
$cfg['Servers'][$i]['savedsearches'] = 'pma__savedsearches';
$cfg['Servers'][$i]['central_columns'] = 'pma__central_columns';
$cfg['Servers'][$i]['designer_settings'] = 'pma__designer_settings';
$cfg['Servers'][$i]['export_templates'] = 'pma__export_templates';

echo "CREATE DATABASE roundcube;" | mysql --defaults-file=/etc/mysql/debian.cnf

apt-get install roundcube roundcube-core roundcube-mysql roundcube-plugins

nano /etc/roundcube/config.inc.php
```
![rccnf](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/rc%20cnf.PNG?raw=true)
