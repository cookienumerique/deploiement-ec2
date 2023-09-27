# Code Deploy

## Installation

Récupération du **bucket-name** et de **l'identifiant région** sur
https://docs.aws.amazon.com/codedeploy/latest/userguide/resource-kit.html


Installation : 

Connection à l'instance

```~/var/scripts/connect-ssh-cookie-numerique.sh```

```
sudo apt update;
sudo apt install ruby-full;
sudo apt install wget;
cd /home/ubuntu; 
wget https://aws-codedeploy-eu-west-3.s3.eu-west-3.amazonaws.com/latest/install;
chmod +x ./install;
sudo ./install auto;
```

Vérifier Code Deploy est installé :

```sudo service codedeploy-agent status```
## Create appspec.yml
)
_deploy.sh_


```
touch ~/var/www/cookie-numerique/deploy.sh;
chmod u+x ~/var/www/cookie-numerique/deploy.sh;
echo '#!/bin/bash
cd /var/www/cookie-numerique || exit;
git pull origin main;
rm -rf node_modules;
rm -f package-lock.json;
rm -f yarn-lock.json;
yarn cache clean
yarn install --verbose;
yarn build --verbose;
pm2 restart cookie_numerique;' > ~/var/www/cookie-numerique/deploy.sh;
```

```
pm2 start "yarn start" --name cookie_numerique
```

_appspec.yml_

```
version: 0.0
os: linux
hooks:
  ApplicationStart:
    - location: deploy.sh
      timeout: 300
      runas: ubuntu
```