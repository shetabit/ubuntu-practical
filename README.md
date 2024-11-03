# ubuntu-practical
Practical Ubuntu linux commands 

### Update and Upgrade
```bash
sudo apt update

sudo apt upgarde
```


### Auto remove and clean
```bash
sudo apt autoremove
//or
sudo apt auto-remove

sudo apt autoclean
//or
sudo apt auto-clean
```

### Install and Remove programs
```bash
//install
sudo apt install app_name

//remove
sudo apt remove app_name

//remove completely
sudo apt remove --purge app_name
```
### Install and Remove deb packages
```bash
//install
sudo dpkg -i /path/to/package.deb

//remove
sudo dpkg -r /path/to/package.deb
```

### Create symlink
```bash
ln -s /path/to/file /path/to/link_name

//example in laravel
ln -s /var/www/html/laravel/storage/app/public /var/www/html/laravel/public/storage

//unlink to remove the link and not where it is pointing at
unlink /path/to/link_name
```

### Alias commands in termeinal
```bash
sudo nano ~/.bashrc
//add your alias
alias alias_name = "original command"
//example
alias art = "php artisan"
alias gp = "git push origin master"

source ~/.bashrc
```
### Repository update error
```bash
Problem:
E: The repository 'http://ppa.launchpad.net/armagetronad-dev/ppa/ubuntu bionic Release' does not have a Release file. 
N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for repository creation and user configuration details.

Solve:
sudo apt-add-repository -r ppa:armagetronad-dev/ppa
sudo apt update -q
```

### Reload network-manager
```bash
sudo systemctl restart network-manager.service
```

### Upload and Download to server via SSH
```bash
//upload
scp [source file] [username]@[destination server]

//download
scp [username]@[destination server]:[local path]

//example
scp -P 3031 /home/projects/project.zip user@217.219.182.39:/var/www/html

scp -P 3031 user@217.219.182.39:/var/www/storage/app/Laravel/2018-04-25-20-45-22.zip /home/hashem/
```
### Transfer file/directories with rsync
```
//simple file
rsync /home/simple.txt root@x.x.x.x:/home

//with directory
rsync -rt /home/transfer_me root@x.x.x.x:/home
```

### Set cronjob
```bash
sudo apt-get update
sudo apt-get install cron

crontab -e
//add your command
* * * * * /usr/bin/php /var/www/domain.com/backup.php > /dev/null 2>&1
```

### Unzip zip files
```bash
sudo apt-get install unzip

unzip file.zip -d destination_folder
```

### Config www directory www-data user in LAMP
```bash
sudo adduser username www-data
sudo chown -R username:www-data /var/www/html

//enable mod_rewrite
sudo a2enmod rewrite

sudo nano /etc/apache2/sites-available/000-default.conf
//append end of file
<Directory /var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

//restart apache
sudo systemctl restart apache2
```

### Apache VirtualHost
```bash
sudo nano /etc/apache2/sites-available/000-default.conf

//Append and save:
<VirtualHost *:80>
  ServerName myapp.dev
  DocumentRoot "/var/www/html/myapp/public"
  <Directory "/var/www/html/myapp/public">
    AllowOverride all
  </Directory>
</VirtualHost>

sudo nano /etc/hosts
//Add 
127.0.0.1 myapp.dev

sudo service apache2 restart
```

### Laravel storage permissions
```bash
sudo chown -R $USER:www-data storage
chmod -R 775 storage
```

### Laravel Installer
```bash
composer global require laravel/installer

sudo nano .bashrc
//append
export PATH="$HOME/.composer/vendor/bin:$PATH"
```

### Install openconnect
```bash
sudo apt-get update
sudo /sbin/modprobe tun
sudo apt-get install openconnect
sudo openconnect SERVER_ADDRESS
```
### Switch php version
```bash
sudo update-alternatives --config php

//disable current php version
sudo a2dismod php8.1

//enable new php version
sudo a2enmod php8.0

sudo systemctl restart apache2
```
### Export & Import large database
```bash
//export
mysqldump -u username -p database_name > data-dump.sql

//import
mysql -u username -p new_database < data-dump.sql
```

### SSH connection error
//WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
```
ssh-keygen -R <server_ip>
```

### Increase PHP Memory Limits
//Edit the PHP.ini File
```
memory_limit = 256M
upload_max_filesize = 12M
post_max_size = 13M
file_uploads = On
max_execution_time = 180
```

### Absolute php & composer commands in server
```
/usr/local/php81/bin/php artisan command

/usr/local/php81/bin/php /usr/local/bin/composer.phar command
```
### Installing and Enabling OPCache

##### 1. Install OPCache: 
```
sudo apt install php8.x-opcache
```
##### 2. Enable OPCache:

Locate php.ini
```
php --ini
```

open php.ini
```
sudo nano /etc/php/8.3/cli/php.ini
```

Edit php.ini
```
zend_extension=opcache

; Recommended OPCache settings
opcache.enable=1
opcache.memory_consumption=256
opcache.interned_strings_buffer=16
opcache.max_accelerated_files=20000
opcache.revalidate_freq=60
opcache.fast_shutdown=1
opcache.enable_cli=1
opcache.validate_timestamps=1
opcache.file_cache=/tmp
opcache.file_update_protection=2
opcache.max_wasted_percentage=5
opcache.opt_debug_level=0
```

And restart apache
```
sudo systemctl restart apache2
```

### My aliases in ubuntu
##### Append these lines in .bashrc or .zshrc file
```
alias www="cd /var/www/html"
alias art="php artisan"
alias laravel="$HOME/.config/composer/vendor/bin/laravel"
alias perm="sudo chown -R $USER:www-data storage && chmod -R 775 storage"
alias apr="sudo systemctl restart apache2"
alias sau="sudo apt update"
alias sax="sudo apt upgrade"
alias cu="composer update"
alias ci="composer install"
```
### Sed command
```
sed 's/\sDEFINER=`[^`]*`@`[^`]*`//g' -i atlas_backup_2023-7-1.sql
```

