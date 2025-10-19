# Exercice-03-Docker
Installation d’un site WordPress avec Docker

Dans ce projet, j’ai créé un environnement complet WordPress à l’aide de Docker Compose.
L’objectif était d’installer la dernière version de WordPress en utilisant les images officielles de Nginx, PHP-FPM et MariaDB, avec un volume commun pour les données et la configuration.

Étapes que j’ai réalisées: 

## 1. Création de la structure du projet

	wordpress-docker/
			─ docker-compose.yml
			─ nginx/
				─ default.conf
			─ wordpress/...	
* Le dossier nginx/ contient la configuration du serveur web.
* Le dossier wordpress/ contient les fichiers WordPress (ils sont créés automatiquement au premier démarrage).

## 2. Création du fichier docker-compose.yml

J’ai créé un fichier docker-compose.yml pour définir les trois services :

* MariaDB pour la base de données, avec un volume persistant.

* PHP-FPM pour exécuter le code PHP de WordPress.

* Nginx comme serveur web, configuré pour rediriger les requêtes vers PHP-FPM.

J’ai également configuré un réseau interne Docker nommé wp-network pour que les conteneurs puissent communiquer entre eux.

## 3. Configuration de Nginx

Dans nginx/default.conf, j’ai configuré le serveur Nginx pour qu’il serve les fichiers WordPress et qu’il redirige correctement les requêtes PHP vers le service php-fpm.
J’ai aussi ajouté des règles de sécurité basiques pour bloquer l’accès aux fichiers cachés (comme .htaccess).

## 4. Installation de WordPress

Dans le service PHP-FPM, j’ai ajouté un script d’installation automatique :

* J’ai téléchargé la dernière version de WordPress depuis le site officiel.

* J’ai décompressé les fichiers dans /var/www/html.

* J’ai installé les extensions PHP nécessaires (mysqli, gd, zip).

* J’ai défini les bons droits sur les fichiers pour l’utilisateur www-data.

Grâce à cette configuration, WordPress s’installe automatiquement au premier démarrage des conteneurs.

## Conclusion

Dans ce projet :

J’ai appris à monter un environnement web complet avec Docker.

J’ai créé et configuré un site WordPress fonctionnel à partir de zéro.

J’ai utilisé des volumes partagés pour rendre l’environnement persistant et modulaire.
