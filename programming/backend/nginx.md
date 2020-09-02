## Install nginx from source with ssl module

```sh
sudo apt update -y && sudo apt install build-essential -y

wget https://nginx.org/download/nginx-1.19.2.tar.gz

tar -zxvf nginx-1.19.2.tar.gz

cd nginx-1.19.2

sudo apt install libpcre3 libpcre3-dev libssl-dev zlib1g-dev -y

./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-debug --with-pcre --with-http_ssl_module

sudo make install

sudo nginx
```

## Add nginx as a service

```sh
cd /etc/init.d

wget https://raw.githubusercontent.com/JasonGiedymin/nginx-init-ubuntu/master/nginx

sudo update-rc.d -f nginx defaults

# /etc/default/nginx
NGINX_CONF_FILE=/etc/nginx/nginx.conf
DAEMON=/usr/bin/nginx

# if service is masked
sudo systemctl unmask nginx.service

sudo service nginx start
```

## Update nginx

Repeat installation process with new version of nginx

```sh
sudo nginx reload

# check 
curl -I http://ip-address
```

## Basic nginx conf

```sh
# /etc/nginx/nginx.conf

events {}

http {
    include mime.types;
    
    server {
        listen 80;
        server_name _;
        root /home/user/www;
    }
}
```

## Location

```sh
server {
    location /home {
       return 200 'hello from home';
    }
}
```

## Exact location

```sh
location = /home {
   return 200 'hello from home';
}
```

## Location with regular expressions

```sh
location ~ /home[0-9] {
   return 200 'hello from home';
}
```

## Location with regular expressions (case insensitive)

```sh
location *~ /home[0-9] {
   return 200 'hello from home';
}
```

## Matching order

1. `=` exact match
2. `^~` preferential prefix
3. `~& *~` regex match
4. `no modifier` prefix match

## Give access to directory

```sh
location /downloads {
    root /www;
    try_files $uri =404;
}
```

## Location specific logs

`error_log`: `stderr | debug | info | notice | warn | error | crit | alert | emerg`

```sh
location /downloads {
    error_log /var/log/nginx/downloads_error.log debug;
    root /www;
    try_files $uri =404;
}
```

## Turn off logs for specific location

```sh
location /downloads {
    access_log off;
    error_log on;
    root /www;
    try_files $uri =404;
}
```

## Workers and other directives

```sh
worker_processes auto;

events {
    worker_connections 1024;
    multi_accept on;
}
```

## Cache

```sh
location ~* \.(css|js|jpg|png|gif) {
    access_log off;
    expires 1M;
    add_header Pragma public;
    add_header Cache-Control public;
    add_header Vary Accept-Encoding;
}
```

## Gzip

```sh
server {
    gzip on;
    # omit file if less than 100b
    gzip_min_length 100;
    # compression between 2-4
    gzip_comp_level 3;
    
    gzip_types text/plain text/javascript text/css
}
```

## FastCGI

```sh
http {
    fastcgi_cache_path /tmp/nginx_cache levels=1:2 keys_zone=microcache:10m max_size=500m;
    fastcgi_cache_key "$scheme$request$_method$host$request_uri";
    # HIT | BYPASS | MISS
    add_header microcache $upstream_cache_status;
    
    location ~ \.php$ {
        include fastcgi_params;
        include fastcgi.conf;
        
        fastcgi_cache microcache;
        fastcgi_cache_valid 200 60m;
        fastcgi_pass 127.0.0.1:9000;
    }
}
```

## Conditional caching

```sh
http {
    server {
        set $no_cache 0;
       
        # Bypass cache for post requests
        if ($request_method = POST) {
            set $no_cache 1;
        }
       
        # Bypass cache for URLs with query string
        if ($query_string != "") {
            set $no_cache 1;
        }
       
        # Bypass cache for the following URL
        if ($request_uri ~* "wp-admin") {
            set $no_cache 1;
        }
        
        location ~ \.php$ {
            fastcgi_cache_bypass $no_cache;
            fastcgi_no_cache $no_cache;
        }
    }
}
```

## Limit concurrency

```sh
http {
    limit_conn_zone $server_name zone=per_vhost:5m;
    limit_conn_zone $binary_remote_addr zone=per_ip:5m;
    
    limit_req_zone $binary_remote_addr zone=one_per_sec:5m rate=1r/s;
}
```

## Basic auth

```sh
sudo apt install apache2-utils

sudo htpasswd -c /etc/nginx/.htpassw user

location ~\.mp4 {
   auth_basic "Restricted";
   auth_basic_user_file /etc/nginx/.htpassw;
}
```

## Security

```sh
./configure --without-http_autoindex_module

http {
    # turn off version
    server_tokens off;
    
    # configure buffer sizes
    client_body_buffer_size 16k;
    client_header_buffer_size 1k;
    client_max_body_size 8m;
    large_client_header_buffers 2 1k;
    
    # block user agents
    # $http_referer
    if ($http_user_agent ~* bot) {
        return 403;
    }
    
    # render iframes on same origin only
    add_header X-Frame-Options SAMEORIGIN;
}
```

## Load balancer

```sh
http {
    upstream servers {
        ip_hash | least_conn;
        server localhost:9001;
        server localhost:9002;
        server localhost:9003;
    }
    server {
        listen 9090;
        proxy_pass http://servers;
    }
}
```

## Links
- [Nginx resources](https://github.com/fcambus/nginx-resources)
- [Common mistakes](https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/)
