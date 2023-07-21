#1. install with binary
$> groupadd mysql
$> useradd -r -g mysql -s /bin/false mysql
$> cd /usr/local
$> tar xvf /path/to/mysql-VERSION-OS.tar.xz
$> ln -s full-path-to-mysql-VERSION-OS mysql
$> cd mysql
$> mkdir mysql-files
$> chown mysql:mysql mysql-files
$> chmod 750 mysql-files
$> bin/mysqld --initialize --user=mysql
$> bin/mysql_ssl_rsa_setup
$> bin/mysqld_safe --user=mysql &
# Next command is optional
$> cp support-files/mysql.server /etc/init.d/mysql.server

#2. binlog show command
mysqlbinlog --base64-output=decode-rows -vv binlog.000001 > log1

#3. drop table by prefix
SET group_concat_max_len = 20000;
select concat("drop table ", GROUP_CONCAT(table_name), ";") as sql1 from information_schema.tables where table_name like "wp_%";  
select concat("drop table ", table_name, ";") as sql1 from information_schema.tables where table_name like "%_wp_%";

#4. create user
create database woo3 default character set utf8mb4 collate utf8mb4_unicode_ci;
create user 'web092722'@'localhost' identified by 'seu.wsu1ds39-Smx#s-6Ds';
grant select,update,insert,delete on woo3.* to 'web092722'@'localhost';
flush privileges;

#5. mysqld conf
sql_mode = STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION

#6. backup
mysqldump -hhostname -uusername -pmypwd databasename > /path to backup/bakname.sql

#7 import settings
	set global max_allowed_packet = 2*1024*1024*10   or max_allowed_packet = 20M in my.cnf
	set global net_read_timeout = 120;
	set global net_write_timeout = 900;

	如果表损坏：innodb_force_recovery = 1 或者 6
	innodb_large_prefix=ON 使用索引超过767字节





