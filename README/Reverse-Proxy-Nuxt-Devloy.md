# __Nuxt-Laravel-Devloy

## Reverse-Proxy-Nuxt-Devloy


````
cd /var/www/html/__Nuxt-Laravel-Devloy/client
npm install pm2 -g
pm2 start npm -- start

sudo vim /etc/nginx/nginx.conf

server {
    listen 8090;
    listen [::]:8090;
    index index.html;
    server_name _;
    root         /var/www/html/__Nuxt-Laravel-Devloy/client/dist;
    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

sudo systemctl restart nginx
````
