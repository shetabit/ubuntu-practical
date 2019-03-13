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
