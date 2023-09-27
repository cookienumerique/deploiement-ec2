1. Installation
```
apt-get update
sudo apt-get install certbot
sudo apt install python3-certbot-nginx
```

2. Obtain the SSL/TLS Certificate
sudo certbot --nginx -d cookie-numerique.fr -d www.cookie-numerique.fr


_Attention au cache du navigateur
_Le cerbot écrit à la suite de la conf nginx_