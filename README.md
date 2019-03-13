# ubuntu-practical
Practical Ubuntu linux commands 

### Update and Upgrade
```bash
sudo apt update

sudo apt upgarde
```

### Install and Remove programs
```bash
//install
sudo apt install app_name

//remove
sudo apt remove app_name

//remove complete
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
