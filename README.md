#Конфиг для nginx

```nginx
server {
    root /home/esherkunov/www/doitwithlove;
    index index.php index.html index.htm;
    server_name doitwithlove.net;
    location =  / {
            try_files /index-en.html =404;
    }
    location = /ru {
            try_files /index-ru.html =404;
    }
    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
            root /usr/share/nginx/www;
    }
    location ~ /\.ht {
            deny all;
    }
}
server {
    server_name www.doitwithlove.net;
    rewrite ^/(.*) http://doitwithlove.net/$1 permanent;
}

