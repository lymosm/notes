#1. install php
./configure --prefix=/usr/local/php --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-openssl --with-zlib --with-curl --enable-ftp --enable-gd --with-webp --with-jpeg --with-xpm --with-freetype --enable-intl --enable-mbstring --with-mysqli=/usr/local/mysql/bin/mysql_config --with-pdo-mysql=/usr/local/mysql --with-zip

or 

./configure --prefix=/usr/local/php --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-openssl --with-zlib --with-curl --enable-ftp --enable-gd --with-webp --with-jpeg --with-xpm --with-freetype --enable-intl --enable-mbstring --with-mysqli=/usr/local/mysql/bin/mysql_config --with-pdo-mysql=/usr/local/mysql --with-zip --with-apxs2=/usr/local/apache/bin/apxs

#2. composer usage
	composer install 
	composer update mypackage/mypackage
	composer require package
	composer search package
	composer init  ==== create your package

#3. install composer
	php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');"
	php composer-setup.php
	php -r "unlink('composer-setup.php');"
	sudo mv composer.phar /usr/local/bin/composer  === linux
	@php "%~dp0composer.phar" %*  === in composer.bat on php bin path of windows

