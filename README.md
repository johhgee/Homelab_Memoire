# SOC Next Gen w/ Open source tools
J'ai rédigé un mémoire ayant pour sujet "Mise en place et gestion d'un SOC automatisé avec des outils open-sources".

Pour se faire, je me suis inspiré d'un projet existant : [SOC-OpenSource](https://github.com/BlackPerl-DFIR/SOC-OpenSource).

Ce dépôt a pour objectif de présenter les outils utilisés ainsi que les processus d'installation et de configuration nécessaires pour mettre en place un SOC automatisé.

## Table des matières
1. [Introduction](#introduction)
2. [Composants](#composants)
    - [TheHive](#thehive)
    - [ELK Stack](#elk-stack)
    - [Cortex](#cortex)
    - [Shuffle](#shuffle)
    - [MISP](#misp)
3. [Pré-requis](#pré-requis)
4. [Installation](#installation)
    - [Installation de TheHive](#installation-de-thehive)
    - [Installation de ELK Stack](#installation-de-elk-stack)
    - [Installation de Cortex](#installation-de-cortex)
    - [Installation de Shuffle](#installation-de-shuffle)
    - [Installation de MISP](#installation-de-misp)
5. [Configuration](#configuration)
    - [Configuration de TheHive](#configuration-de-thehive)
    - [Configuration de ELK Stack](#configuration-de-elk-stack)
    - [Configuration de Cortex](#configuration-de-cortex)
    - [Configuration de Shuffle](#configuration-de-shuffle)
    - [Configuration de MISP](#configuration-de-misp)
6. [Scénarios d'Automatisation](#scénarios-dautomatisation)
    - [Playbook de Détection et Réponse à un Mail de Phishing](#playbook-de-détection-et-réponse-à-un-mail-de-phishing)

## Introduction

Ce dépôt présente les outils nécessaires et les étapes pour créer un SOC Next Gen en utilisant des outils open source. Chaque composant du SOC est détaillé avec des instructions d'installation et de configuration.

## Composants

### TheHive
TheHive est une plateforme de gestion d'incidents de sécurité. Elle permet de centraliser les alertes et de créer des cas pour une gestion efficace des incidents.

### ELK Stack
ELK Stack (Elasticsearch, Logstash, Kibana) est une suite d'outils pour la gestion et l'analyse des logs. Elle permet de collecter, stocker et visualiser les données de sécurité.

### Cortex
Cortex est une plateforme d'analyse de sécurité qui permet d'exécuter des actions analytiques sur les observables (IP, URL, fichiers, etc.).

### Shuffle
Shuffle est un outil d'orchestration et d'automatisation qui permet de créer des workflows pour automatiser les réponses aux incidents de sécurité.

### MISP
MISP (Malware Information Sharing Platform) est une plateforme de partage d'informations sur les menaces. Elle permet de collecter, stocker et partager des informations sur les indicateurs de compromission (IOC).

## Pré-requis

Dans mon cas, j'ai une machine avec 32 Go de RAM et 1 To de stockage.
J'ai utilisé VM Ware pour virtualiser les serveurs voici les configurations de chaque vm :

- MISP : 2 vCPUs, 4 Go de RAM, 30 à 50 Go de stockage
- Elastic SIEM : 2 vCPUs, 8 Go de RAM, 30 à 50 Go de stockage
- Cortex : 2 vCPUs, 4 Go de RAM, 30 à 50 Go de stockage
- TheHive : 2 vCPUs, 4 Go de RAM, 30 à 50 Go de stockage
- Shuffle : 2 vCPUs, 8 Go de RAM, 30 à 50 Go de stockage

## Installation

### Installation de TheHive
1. Téléchargez et installez TheHive depuis le [site officiel](https://thehive-project.org/).
2. Configurez TheHive en suivant la documentation fournie.

### Installation de ELK Stack
1. Téléchargez et installez Elasticsearch, Logstash et Kibana depuis le [site officiel](https://www.elastic.co/elk-stack).
2. Configurez chaque composant en suivant les guides d'installation.

### Installation de Cortex
1. Téléchargez et installez Cortex depuis le [site officiel](https://thehive-project.org/).
2. Configurez Cortex pour qu'il fonctionne avec TheHive.

### Installation de Shuffle
1. Téléchargez et installez Shuffle depuis le [site officiel](https://shuffler.io/).
2. Configurez les workflows nécessaires pour l'automatisation des tâches.

### Installation de MISP
1. Téléchargez et installez MISP depuis le [site officiel](https://www.misp-project.org/).
2. Configurez MISP pour qu'il puisse partager et recevoir des informations sur les menaces.

## Configuration

### Configuration de TheHive
1. Configurez les connecteurs pour intégrer TheHive avec Cortex, MISP et autres outils.
2. Définissez les règles de création de cas et d'alertes.

### Configuration de ELK Stack
1. Configurez les pipelines de données dans Logstash pour collecter les logs de sécurité.
2. Créez des tableaux de bord dans Kibana pour visualiser les données.

### Configuration de Cortex
1. Ajoutez des analyzers et responders pour automatiser l'analyse des observables.
2. Intégrez Cortex avec TheHive pour envoyer les résultats d'analyse.

### Configuration de Shuffle
1. Créez des workflows pour automatiser les réponses aux incidents.
2. Intégrez Shuffle avec TheHive et Cortex pour orchestrer les tâches.

### Configuration de MISP
1. Configurez les feeds et les API pour recevoir et partager des IOC.
2. Intégrez MISP avec TheHive pour enrichir les cas avec des informations sur les menaces.

## Scénarios d'Automatisation

### Playbook de Détection et Réponse à un Mail de Phishing

Ce playbook décrit les étapes automatisées pour détecter et répondre à un email de phishing. Il inclut la réception d'une alerte ELK, la création d'une alerte dans TheHive, l'analyse avec Cortex, et la notification de l'équipe via Microsoft Teams. Des actions correctives sont ensuite orchestrées par Shuffle, et un rapport final est généré dans TheHive.