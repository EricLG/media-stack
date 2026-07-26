# Ugreen Media Stack

## Services

- Jellyfin
- Sonarr
- Radarr
- Prowlarr
- RDT-Client
- Recyclarr

## Prérequis

- Docker Compose
- AllDebrid
- Un indexeur configuré dans Prowlarr

## Installation

git clone ...
cp .env.example .env
Modifier le .env
docker compose up -d

## Mise à jour

git pull
docker compose pull
docker compose up -d

## Sauvegarde

Sauvegarder :
- config/
- .env

Les médias et téléchargements ne font pas partie du dépôt.

## Recyclarr

Synchronisation manuelle :

docker compose run --rm recyclarr sync

Ou via une tâche planifiée du NAS.

## Arborescence

config/
docs/

Les médias sont stockés dans :
/volume1/Videos

Les téléchargements dans :
/volume1/Downloads
