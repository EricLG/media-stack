# Ugreen Media Stack

## Objectif

Stack Docker permettant d'automatiser la gestion d'une bibliothèque multimédia Jellyfin :

- Recherche de releases : Prowlarr
- Gestion des films : Radarr
- Gestion des séries : Sonarr
- Téléchargement via débrideur : rdtclient + AllDebrid
- Serveur multimédia : Jellyfin

Architecture basée sur Docker Compose sur le NAS Ugreen DXP4800 Plus.

---

## Arborescence principale


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


---

## Permissions Docker / LinuxServer.io

Les conteneurs LinuxServer.io (Radarr, Sonarr, Prowlarr) utilisent :
- PUID=1003
- PGID=100

Les dossiers de configuration doivent appartenir à cet utilisateur pour éviter les erreurs :
`AppFolder /config is not writable`
ou
`Permission denied /data/db`

Réinitialisation des droits :

```bash
sudo chown -R 1003:100 /volume1/docker/media-stack/config/radarr
sudo chown -R 1003:100 /volume1/docker/media-stack/config/sonarr
sudo chown -R 1003:100 /volume1/docker/media-stack/config/prowlarr
sudo chown -R 1003:100 /volume1/docker/media-stack/config/rdtclient

sudo chmod -R 775 /volume1/docker/media-stack/config/radarr
sudo chmod -R 775 /volume1/docker/media-stack/config/sonarr
sudo chmod -R 775 /volume1/docker/media-stack/config/prowlarr
sudo chmod -R 775 /volume1/docker/media-stack/config/rdtclient
