# Проект 01 — Static site + Nginx + HTTPS

## Локально (на Mac)
В репозитории лежат:
- site/index.html — страница сайта
- nginx/site-http.conf — конфиг nginx для HTTP (до certbot)

## Deploy (на VPS)
1) Установить nginx:
   sudo apt update
   sudo apt install -y nginx

2) Скопировать index.html на VPS в /var/www/static-site/index.html

3) Скопировать nginx конфиг в:
   /etc/nginx/sites-available/static-site

4) Включить сайт:
   sudo ln -sf /etc/nginx/sites-available/static-site /etc/nginx/sites-enabled/static-site
   sudo rm -f /etc/nginx/sites-enabled/default
   sudo nginx -t
   sudo systemctl reload nginx

5) (Когда будет домен) Выпустить HTTPS:
   sudo apt install -y certbot python3-certbot-nginx
   sudo certbot --nginx -d DOMAIN -d www.DOMAIN
