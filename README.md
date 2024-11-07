# Instalasi LAMP Stack (PHP, Apache, MySQL, phpMyAdmin, Composer, Git)

Dokumen ini menjelaskan langkah-langkah untuk menginstal dan mengonfigurasi LAMP stack (Linux, Apache, MySQL, PHP) pada sistem berbasis Ubuntu, beserta instalasi phpMyAdmin, Composer, dan Git.

## Prasyarat
- Sistem operasi Ubuntu (atau distribusi Debian-based lainnya).
- Akses root atau sudo untuk menginstal paket dan melakukan konfigurasi.
- Koneksi internet aktif untuk mengunduh paket.

---

## 1. Instalasi PHP Versi Terbaru

Langkah pertama adalah menginstal PHP beserta beberapa modul yang dibutuhkan untuk pengembangan aplikasi web berbasis PHP.

```bash
sudo apt-get install -y php-cli php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-bcmath git neofetch nala

# Update paket sistem
sudo nala update

# Instalasi MySQL Server
sudo nala install mysql-server

# Masuk ke MySQL sebagai pengguna root
sudo mysql

# Ubah password root MySQL dan atur metode autentikasi
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
exit

# Menjalankan skrip keamanan MySQL untuk mengonfigurasi password dan pengaturan lainnya
sudo mysql_secure_installation


# Update paket sistem
sudo nala update

# Instalasi phpMyAdmin dan beberapa dependensi
sudo nala install phpmyadmin php-mbstring php-zip php-gd php-json php-curl

# Selanjutnya, ikuti instruksi di layar untuk mengonfigurasi phpMyAdmin, termasuk mengonfigurasi Apache dan membuat database phpMyAdmin jika diminta.


# Mengunduh dan menginstal Composer
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

# Pindahkan file composer.phar ke direktori bin untuk dapat digunakan secara global
sudo mv composer.phar /usr/local/bin/composer

# Update sistem untuk memastikan semua dependensi terinstal dengan benar
sudo nala update


# Mengonfigurasi nama pengguna Git
git config --global user.name "Nama Anda"

# Mengonfigurasi alamat email pengguna Git
git config --global user.email "email@domain.com"
