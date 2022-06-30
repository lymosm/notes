#1. install
1. git clone file
2. exec script: bin/magento setup:install --base-url=https://jms.magento.com --db-host=127.0.0.1 --db-name=magento --db-user=magento --db-password=Magento123456. \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123456 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=elasticsearch7 \
--elasticsearch-host=127.0.0.1 \
--elasticsearch-port=9200 \
--elasticsearch-index-prefix=magento \
--elasticsearch-timeout=15
3. set web root to ./setup/ for web page install
4. set web root to ./pub
5. chmod folder 
6. change version1656622318 static folder

#2. backend uri: /admin_z4ni5c
