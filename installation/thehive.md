# Procédure d'installation de TheHive + Cortex + Shuffle avec ansible et docker

Installation réalisée à partir de https://github.com/TheHive-Project/Docker-Templates/

1. Modifier le fichier `.env` dans `files/misp/.env` et customiser les configurations.
2. Customiser le playbook ansible `playbooks/install_misp.yml` et le fichier d'inventaire `hosts.ini`
3. Déployer le playbook ansible avec la commande suivante 
```
ansible-playbook playbooks/install_thehive_cortex_shuffle.yml -i hosts.ini -l nom_du_serveur --diff -K
```
4. Se connecter au serveur, aller dans le dossier misp et lancer la commande suivante
```
docker compose up -d
```
5. Se connecter sur `http://localhost` ou l'adresse IP du serveur sur le port `9001`.
6. Créer un organisation cortex et un utilisateur avec une clé API
7. Sauvegarer la clé API dans `vol/thehive/application.conf`
8. Redémarrer le container avec ``docker-compose down && docker-compose up -d``

Voici les différents port pour les services 

- TheHive : 9000
- Cortex : 9001
- Shuffle : 3001