# Deploiement EC2

## Création d'une instance EC2

1. Ubuntu
2. Création d'une paire de clef : même nom que le projet et l'enregistrer dans 

> /var/keypair

3. Mettre le fichier en lecture seule
`chmod 400 cookie-numerique.pem`

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

1. Dans instance le détail de l'instance copier DNS **IPv4 public**
2. Créer un script pour se connecter à l'instance dans **/var/scripts** :

Création du fichier et droit d'execution

`cd /var/scripts:`

`sudo touch connect-ssh-cookie-numerique.sh;`

`sudo chmod u+x connect-ssh-cookie-numerique.sh;`

Script de connexion

`cd /var/keypair;`

`ssh -i "<YOUR-KEY-NAME>.pem" ubuntu@<YOUR-COPIED-PUBLIC-IPv4-ADDRESS>`

3. Configuration du serveur

`sudo apt upgate;`

### Installation de nginx
`sudo apt install nginx;`

### Installation de node
`wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
source ~/.bashrc
nvm install --lts
`
