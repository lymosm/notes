#1. install
./configure --user=www --group=www --with_http_ssl_module --with_http_v2_module --with-http_stub_status_module

#2. rewrite try_files
try_files $uri $uri/ /index.php?$args;

#3. ssl server conf
server {
        listen 80;
        server_name ming.wp.com;
        rewrite ^(.*)$ https://${server_name}$1 permanent;
}

server {
        listen      443 ssl;
        server_name ming.wp.com;
        root        /www/ming.wp.com;
        ssl_certificate /usr/local/nginx/ssl/ming.wp.com.crt;
        ssl_certificate_key /usr/local/nginx/ssl/ming.wp.com.key;

        location / {
            index   index.php index.html index.htm;
                try_files $uri $uri/ /index.php?$query_string;
        }

        location ~* \.php {
            include                 fastcgi_params;
            fastcgi_index           index.php;
            fastcgi_pass            127.0.0.1:9000;
            fastcgi_split_path_info ^(.+\.php)(.*)$;
            fastcgi_param           PATH_INFO       $fastcgi_path_info;
            fastcgi_param           SCRIPT_NAME     $fastcgi_script_name;
            fastcgi_param           SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
    }

#4. proxy

    location / {
        proxy_pass http://127.0.0.1:8080/;
        proxy_set_header    Host               $host:$server_port;
        proxy_set_header    Remote_Addr        $remote_addr;
        proxy_set_header    X-Real-IP          $remote_addr;
        proxy_set_header    X-Forwarded-For    $proxy_add_x_forwarded_for;
        proxy_set_header    X-Forwarded-Proto  $scheme;
        proxy_set_header    X-Nginx-Proxy      true;
        
        # index页面设置
        index index;
    }

#5. 配置jpg png静态不走php (可用于wordpress)

    location / {
        try_files $uri $uri/ @rewriteapp;
        index   index.php index.html index.htm;
    }
    location @rewriteapp {
        if ( $request_filename !~* \.(jpg|png)$ ) {
            rewrite ^(.*)$ /index.php/$1 last;
        }
    }

#6. 