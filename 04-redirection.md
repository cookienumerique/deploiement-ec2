1. Redirection :
    - Type A - @ cible IP V4
    - Type A - www - cible IP V4

2. Configuration NGINX : 

Editer ```nano /etc/nginx/sites-available```

Changer le root : 
```root /var/www/cookie-numerique;```

```
# Fichiers statics
location /_next/static {
        add_header Cache-Control "public, max-age=3600, immutable";
        proxy_pass http://127.0.0.1:3000/_next/static;
}
        
location / {
                proxy_pass http://localhost:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }

```

Restart nginx : ```sudo systemctl restart nginx```
