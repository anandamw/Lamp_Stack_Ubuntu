# LAMP Stack Installation (PHP, Apache, MySQL, phpMyAdmin, Composer, Git)

This document describes the steps to install and configure the LAMP stack (Linux, Apache, MySQL, PHP) on an Ubuntu-based system, along with the installation of phpMyAdmin, Composer, and Git.

## Prerequisites
- Ubuntu operating system (or other Debian-based distribution).
- Root or sudo access to install packages and perform configuration.
- Active internet connection to download the package.

---

## Installing the latest version of PHP

The first step is to install PHP along with several modules required for PHP-based web application development.


```bash
# Install PHP and related packages
sudo apt-get install -y php-cli php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-bcmath git neofetch nala apache2  libapache2-mod-php

# Update system packages
sudo nala update

# Allow Apache through the firewall
sudo ufw allow 'Apache'

# Install MySQL Server
sudo nala install mysql-server

# Log in to MySQL as root user
sudo mysql

# Change the MySQL root password and set the authentication method
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
exit

# Run the MySQL security script to configure password and other settings
sudo mysql_secure_installation

# Update system packages again
sudo nala update

# Install phpMyAdmin and additional dependencies
sudo nala install phpmyadmin php-mbstring php-zip php-gd php-json php-curl

# Follow the on-screen instructions to configure phpMyAdmin, including setting up Apache and creating the phpMyAdmin database if prompted.

# Download and install Composer
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

# Move the composer.phar file to the bin directory for global usage
sudo mv composer.phar /usr/local/bin/composer

# Update the system to ensure all dependencies are properly installed
sudo nala update

# Configure Git username
git config --global user.name "Your Name"

# Configure Git email
git config --global user.email "email@domain.com"

