# Server Setup Instructions
Use these instructions to setup Apache, PHP,Composer, And Node JS in your Ubuntu System

## Requirments
Here I am using an Ubuntu server. So these commands will only work on Ubuntu Server.

## Installation
To install Apache

```bash
sudo apt-get install apache2
```
After the installation complete, go to your preferred browser, type in the address bar

```bash
http://localhost
```
and hit enter. You should see Ubuntu's default page on your screen.

Then go back to your terminal and type

```bash
sudo apt-get install php php-curl php-xml libapache2-mod-php php-mysql php-mbstring php-fpm
```
After installing these packages,type
```bash
cd var/www/html
```
It brings you to your server folder.Then type
```bash
sudo nano test.php 
```
It will open a terminal-based text editor, then type

```bash
<?php echo "IT WORKS" ?>
```
and then press ```ctrl```+```s``` and ```ctrl```+```x```. After that go to your browser again and type on addressbar.

```bash
http://localhost/test.php
```
It should say "IT WORKS"

And now it's time to set up the MySQL database. Go back to terminal  
```bash
sudo apt-get install mysql-server mysql-client
```
After install MySQL server , I am going to set up my MySQL root password, type
```bash
sudo mysql
```
If it wants a password then type your system user password.After entering into MySQL terminal, type
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
```
Put your password in ```your_password``` field. Then type 
```bash
FLUSH PRIVILEGES
```
Again type and hit enter
```bash
quit;
```
MySQL setup is done.

Now it's time to install Node JS
```bash
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install nodejs
```
To check Node version
```bash
node -v
```

To check npm version
```bash
npm -v
```

## Yarn
Yarn is a Node JS package manager like NPM. To install Yarn
```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update
sudo apt-get install yarn
```
To check Yarn version
```bash
yarn -v
```

## Composer
Like Yarn, Composer is a package manager, But it's for PHP. To setup composer in your machine 

```bash
sudo apt update
sudo apt-get install php-cli php-zip unzip
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" 
HASH="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php -r "unlink('composer-setup.php');"
```
It will install Composer in your system. To access it easily, run this command

```bash
sudo mv composer.phar /usr/local/bin/composer
```
After that, Simply type 

```bash
composer
```
And hit enter. You can see its nice function list and work doc in your terminal.


## Special Commands
1. To change the PHP version, use this command
```bash
sudo update-alternatives –config php 
```
then choose your PHP version and enter. Then type 
```bash
sudo a2enmod 'your_php_version'
```
