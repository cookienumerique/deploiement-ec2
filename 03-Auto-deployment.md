# Auto deployment

## Create an IAM Role for CodeDeploy

1. Dans le dashboard IAM : 
- Role > create role
- AWS service
- CodeDeploy

2. Informations du rôle
- Nom : service-role-for-code-deploy

## Create an IAM Role for EC2

1. Dans le dashboard IAM :
- Role > create role
- Service ou cas d'utilisation : **EC2**
- Politique des autorisations : **AmazonEC2RoleforAWSCodeDeploy**

2. Informations du rôle
- Nom : code-deploy-role-for-ec2

## Attach the IAM Role to EC2
Sur le page de l'instance EC2
- Actions > Sécruité > Modifier le rôle IAM
- Sélectionner **"code-deploy-role-for-ec2"**
- Redémarrer instance