# Deploiement EC2

## Création d'une instance EC2
Choix de l'instance ici : https://www.padok.fr/blog/instance-ec2-aws
1. Ubuntu
2. Création d'une paire de clef : même nom que le projet et l'enregistrer dans 

> ~/var/keypair

3. Mettre le fichier en lecture seule

`chmod 400 ~/var/keypair/cookie-numerique.pem`

4. Dans paramètre réseau :
    - Autoriser SSH (anywhere), HTTP et HTTPS
    - Cliquer sur éditer et ajouter une règle de groupe :
      - TCP personnnalisé
      - port 3000 
      - source 0.0.0.0/0

5. Configurer le stockage : 
    - 20Go

6. Lancer l'instance


## Accéder à l'instance

1. Création d'un script pour se connecter à l'instance dans **~/var/scripts** :
```
mkdir ~/var/scripts;
cd ~/var/scripts;
touch connect-ssh-cookie-numerique.sh;
echo 'cd ~/var/keypair && ssh -i <YOUR-KEY-NAME>.pem ubuntu@<YOUR-COPIED-PUBLIC-IPv4-ADDRESS>' > ~/var/scripts/connect-ssh-cookie-numerique.sh;
chmod u+x ~/var/scripts/connect-ssh-cookie-numerique.sh;
```

2. Configuration du serveur

```
sudo apt update;
sudo apt install nginx;
sudo apt install yarn;
npm install pm2 -g;
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
source ~/.bashrc
nvm install --lts;
sudo chown ubuntu:ubuntu /var/www;
```
