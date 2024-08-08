# Procédure d'installation de MISP avec ansible et docker

1. Modifier le fichier .env dans *files/misp/.env* et customiser les configurations.
2. Customiser le playbook ansible *playbooks/install_misp.yml* et le fichier d'inventaire *hosts.ini*
3. Déployer le playbook ansible avec la commande suivante 
```
ansible-playbook playbooks/install_misp.yml -i hosts.ini -l nom_du_serveur --diff -K
```
4. Se connecter au serveur, aller dans le dossier misp et lancer la commande suivante
```
docker compose up -d
```
5. Se connecter sur http://localhost ou l'adresse mentionnée dans la variable MISP_BASEURL dans .env 

Installation réalisée à partir de https://github.com/MISP/misp-docker