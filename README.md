1. Download <i>[Nextcloud](https://nextcloud.com/install/)</i>, <i>[ownCloud](https://owncloud.org/download/)</i> and this repository
```
wget https://download.nextcloud.com/server/releases/latest.tar.bz2 -O /tmp/nextcloud_latest.tar.bz2
wget https://download.owncloud.org/community/owncloud-latest.tar.bz2 -O /tmp/owncloud_latest.tar.bz2
mkdir /var/www/nextcloud /var/www/owncloud
chown -R www-data:www-data /var/www/nextcloud /var/www/owncloud
sudo -u www-data tar -jxvf /tmp/nextcloud_latest.tar.bz2 -C /var/www/
sudo -u www-data tar -jxvf /tmp/owncloud_latest.tar.bz2 -C /var/www/
sudo -u www-data mkdir nextcloud/data owncloud/data
wget https://github.com/xg590/ownCloud/archive/master.zip
unzip master.zip
cd ownCloud-master 
```
2. Setup automatic configuration 
```
sed -i 's/Here_should_be_your_domain_name/your_domain_name/g' docker-compose.yml http/000-default.conf
cp autoconfig.php /var/www/nextcloud/config/autoconfig.php 
sed 's/nextcloud/owncloud/g' /var/www/nextcloud/config/autoconfig.php > /var/www/owncloud/config/autoconfig.php
chown -R www-data:www-data /var/www/nextcloud/config/autoconfig.php /var/www/owncloud/config/autoconfig.php 
```
3. Fire up docker images 
``` 
docker-compose up
```
