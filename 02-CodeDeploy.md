# Code Deploy

## Installation

Récupération du **bucket-name** et de **l'identifiant région** sur
https://docs-aws-amazon-com.translate.goog/codedeploy/latest/userguide/resource-kit.html?_x_tr_sl=auto&_x_tr_tl=fr&_x_tr_hl=fr#resource-kit-bucket-names


Installation : 

Connection à l'instance

```~/var/scripts/connect-ssh-cookie-numerique.sh```

```
sudo apt update;
sudo apt install ruby-full;
sudo apt install wget;
cd /home/ubuntu; 
wget https://aws-codedeploy-eu-north-1.s3.eu-north-1.amazonaws.com/latest/install;
chmod +x ./install;
sudo ./install auto;
```

Vérifier Code Deploy est installé :

```sudo service codedeploy-agent status```
## Create appspec.yml

_deploy.sh_


```
touch ~/var/www/cookie-numerique/deploy.sh;
chmod u+x ~/var/www/cookie-numerique/deploy.sh;
echo '#!/bin/bash
cd /var/www/cookie-numerique;
git pull origin master;
yarn install && yarn build && pm2 restart cookie-numerique' > ~/var/www/cookie-numerique/deploy.sh;
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