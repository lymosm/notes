#1. install php
./configure --prefix=/usr/local/php --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-openssl --with-zlib --with-curl --enable-ftp --enable-gd --with-webp --with-jpeg --with-xpm --with-freetype --enable-intl --enable-mbstring --with-mysqli=/usr/local/mysql/bin/mysql_config --with-pdo-mysql=/usr/local/mysql --with-zip

or 

./configure --prefix=/usr/local/php --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-openssl --with-zlib --with-curl --enable-ftp --enable-gd --with-webp --with-jpeg --with-xpm --with-freetype --enable-intl --enable-mbstring --with-mysqli=/usr/local/mysql/bin/mysql_config --with-pdo-mysql=/usr/local/mysql --with-zip --with-apxs2=/usr/local/apache/bin/apxs

#2. 
