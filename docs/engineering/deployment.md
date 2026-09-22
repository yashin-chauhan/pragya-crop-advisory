# 🚀 Engineering: Deployment & Server Configuration

This document provides deployment guidelines, server hardening specifications, and environment configuration for the Pragya Crop Advisory API.

---

## 1. Production Requirements

- **Operating System:** Ubuntu 22.04 LTS / Debian 11
- **Web Server:** Nginx (>= 1.18)
- **PHP Engine:** PHP 8.1+ with extensions: `php8.1-fpm`, `php8.1-mysql`, `php8.1-mbstring`, `php8.1-xml`, `php8.1-curl`, `php8.1-zip`
- **Database Server:** MySQL 8.0+ / MariaDB 10.6+

---

## 2. Nginx Virtual Host Configuration

```nginx
server {
    listen 80;
    server_name api.cropadvisory.pragya.org;
    root /var/www/pragya-api/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";
    add_header X-XSS-Protection "1; mode=block";

    index index.php;
    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
        fastcgi_hide_header X-Powered-By;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```

---

## 3. Production Deployment Commands

```bash
# 1. Pull latest release
git pull origin master

# 2. Install production dependencies without dev tools
composer install --no-dev --optimize-autoloader

# 3. Cache configuration and routes for high throughput
php artisan config:cache
php artisan route:cache
php artisan view:cache

# 4. Run database migrations
php artisan migrate --force

# 5. Restart PHP-FPM to load fresh opcache
sudo systemctl restart php8.1-fpm
sudo systemctl reload nginx
```
