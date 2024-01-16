# VPN Docker Containers avec StrongSwan

Ce dépôt contient les fichiers nécessaires pour configurer et exécuter deux conteneurs Docker, nommés Bob et Alice, qui établissent un tunnel VPN sécurisé entre eux en utilisant StrongSwan.

## Aperçu
Les conteneurs Bob et Alice sont configurés avec StrongSwan pour créer un tunnel VPN IPsec. Chaque conteneur est configuré avec une adresse

IP statique unique dans un réseau Docker dédié. Le tunnel VPN est sécurisé avec une clé pré-partagée (PSK) générée automatiquement.

## Structure du Projet
`docker-compose.yml`: Fichier Docker Compose pour orchestrer la construction et le démarrage des conteneurs Docker.

`BOB/`:

  * `Dockerfile`: Fichier de construction Docker pour le conteneur Bob.
  
  * `ipsec.conf`: Configuration IPsec pour Bob.
  
`ALICE/`:

  * `Dockerfile`: Fichier de construction Docker pour le conteneur Alice.
  
  * `ipsec.conf`: Configuration IPsec pour Alice.
  
Prérequis

Pour utiliser ce projet, vous devez avoir Docker et Docker Compose installés sur votre machine. 

Veuillez consulter <a href="https://docs.docker.com/">la documentation Docker</a> pour les instructions d'installation.

## Démarrage Rapide
Cloner le Dépôt :

```
git clone https://github.com/quentinvvn/StrongSwan_IPSec_PSK.git
cd StrongSwan_IPSec_PSK
```

Construire et Démarrer les Conteneurs :

```
docker-compose up --build
```

Vérifier l'État du Tunnel VPN :

  * Accédez à l'un des conteneurs :
  ```
  docker exec -it nom_du_conteneur bash
  ```
  * Vérifiez l'état de la connexion IPsec :
  ```
  ipsec status
  ```

## Configuration 
* StrongSwan :
  * Les configurations IPsec spécifiques sont définies dans les fichiers ipsec.conf dans les dossiers BOB et ALICE.

  * Les clés pré-partagées sont spécifiées dans les fichiers ipsec.secrets.

## Sécurité

Ce projet est destiné à des fins de démonstration. Pour une utilisation en production, assurez-vous de suivre les meilleures pratiques en matière de sécurité, notamment en gérant les clés de manière sécurisée.
