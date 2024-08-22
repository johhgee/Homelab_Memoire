# Installation de TheHive + Cortex + MISP

J'ai utilisé ce fichier de configuration https://github.com/ls111-cybersec/thehive-cortex-misp-docker-compose-lab11update/blob/main/docker-compose.yml que j'ai customisé

## Instructions 

Envoi des fichiers vers le serveur 
```
ansible-playbook playbooks/install_thehive_cortex_misp.yml -l xxxx -i hosts.ini  --diff
```

Puis sur le serveur cible

```
cd TCM
vim .env # Pour configurer le fichier pour définir des variables
docker compose up -d
```

### TheHive

The Hive: http://x.x.x.x:9000

Se connecter avec admin:secret

### Cortex

Cortex: http://x.x.x.x:9001

Cliquer sur mettre à jour la base, créer un compte puis se connecter
Création d'une Organisation
Création d'un utilisateur
Récupération de l'API

### MISP

MISP: http://x.x.x.x

Se connecter avec admin@admin.test:admin
Création d'une Organisation
Création d'un utilisateur admin pour l'Organisation
Récupération de l'AuthKey