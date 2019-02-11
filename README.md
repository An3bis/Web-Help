# MySQL - Create new user
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';

flush privileges;
# MySQL - Disable password validation

uninstall plugin validate_password;

# Composer - global install

sudo apt update

sudo apt install curl php-cli php-mbstring git unzip

cd ~

curl -sS https://getcomposer.org/installer -o composer-setup.php

https://getcomposer.org/download/ (copy 2 line with hash)

sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer 

# Composer - create json file

composer require vendor/package

# Composer - set-up Laravel

composer global require laravel/installer

# Laravel - create site

sudo composer create-project --prefer-dist laravel/laravel blog
