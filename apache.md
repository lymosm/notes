1. ssl server config
#<Directory "/var/www/html/esrgear.com-20210727/">   
 #     Options +Indexes FollowSymLinks   
  #    AllowOverride all   
#</Directory> 
<VirtualHost *:443>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName lo.wp.com
        ServerAlias lo.wp.com

        ServerAdmin webmaster@localhost
        DocumentRoot /mnt/d/www/esrgear.com

        DirectoryIndex index.html index.php
        <Location "/sdk">
                Deny from all
        </Location>

        #SSLEngine on
        #SSLCertificateFile /etc/apache2/ssl2/02.pem
        #SSLCertificateKeyFile /etc/apache2/ssl2/server.key
        #SSLCertificateChainFile /etc/apache2/ssl2/chain.crt
SSLEngine on
   SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
   SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

2. 