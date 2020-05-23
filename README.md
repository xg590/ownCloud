1. Download <i>[Nextcloud](https://nextcloud.com/install/)</i> and <i>[ownCloud](https://owncloud.org/download/)</i>
```
wget https://download.nextcloud.com/server/releases/latest.tar.bz2 -O /tmp/nextcloud_latest.tar.bz2
wget https://download.owncloud.org/community/owncloud-latest.tar.bz2 -O /tmp/owncloud_latest.tar.bz2
mkdir /var/www/nextcloud /var/www/owncloud
chown -R www-data:www-data /var/www/nextcloud /var/www/owncloud
sudo -u www-data tar -jxvf /tmp/nextcloud_latest.tar.bz2 -C /var/www/
sudo -u www-data tar -jxvf /tmp/owncloud_latest.tar.bz2 -C /var/www/

```
2. Setup automatic configuration 
```
cat << EOF > /var/www/nextcloud/config/autoconfig.php
<?php
$AUTOCONFIG = array(
  "dbtype"        => "mysql",
  "dbname"        => "dbname",
  "dbuser"        => "username",
  "dbpass"        => "passwd",
  "dbhost"        => "db:3306",
  "dbtableprefix" => "",
  "adminlogin"    => "admin_name",
  "adminpass"     => "admin_passwd",
  "directory"     => "/var/www/nextcloud/data",
); 
EOF
sed 's/nextcloud/owncloud/g' /var/www/nextcloud/config/autoconfig.php > /var/www/owncloud/config/autoconfig.php
```
3. Fire up docker images 
