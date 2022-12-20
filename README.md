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
scp /home/projects/project.zip user@217.219.182.39:/var/www/html

scp  user@217.219.182.39:/var/www/storage/app/Laravel/2018-04-25-20-45-22.zip /home/hashem/
```
###Transfer file/directories with rsync
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
```
