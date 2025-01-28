# 🎬 Docker Media Stack (Plex, Sonarr, Radarr, qBittorrent...)

Ce projet met en place une stack complète pour la gestion multimédia basée sur Docker. Il inclut Plex, Sonarr, Radarr, qBittorrent, et d'autres outils pour gérer vos médias.

---

## 📌 **Services inclus**
- **Plex** : Serveur multimédia
- **Sonarr** : Gestionnaire de séries
- **Radarr** : Gestionnaire de films
- **Bazarr** : Gestion des sous-titres
- **Lidarr** : Gestionnaire de musique
- **Readarr** : Gestionnaire de livres/audio
- **qBittorrent** : Client torrent sécurisé
- **Jackett** : Proxy d'indexeurs torrent
- **Prowlarr** : Gestion des indexeurs pour Sonarr/Radarr
- **Flaresolverr** : Résolution de captchas
- **Tautulli** : Statistiques et monitoring de Plex
- **Gluetun** : VPN sécurisé (Mullvad via WireGuard)

---

## 🛠 **Pré-requis**

Avant de commencer, assurez-vous d'avoir :
- **Docker et Docker Compose** installés sur votre machine.
- **Un dossier dédié pour stocker les volumes des conteneurs.**

### 📂 **Créer les dossiers nécessaires**
Exécutez les commandes suivantes pour créer les dossiers :
```sh
mkdir -p /volume2/docker/Plex
mkdir -p /volume2/docker/qbittorrent/config
mkdir -p /volume2/docker/sonarrv3
mkdir -p /volume2/docker/radarr
mkdir -p /volume2/docker/bazarr
mkdir -p /volume2/docker/prowlarr
mkdir -p /volume2/docker/jackett
mkdir -p /volume2/docker/readarr
mkdir -p /volume2/docker/lidarr
mkdir -p /volume2/SEEDBOX/FILMS
mkdir -p /volume2/SEEDBOX/SERIES
mkdir -p /volume2/SEEDBOX/Downloads/InProgress
mkdir -p /volume2/SEEDBOX/Downloads/movies
mkdir -p /volume2/SEEDBOX/Downloads/readarr
mkdir -p /volume2/SEEDBOX/Downloads/tv
mkdir -p /volume2/SEEDBOX/COMICS
mkdir -p /volume2/docker/audiobookshelf/audiobooks
```

---

## 🚀 **Installation**

### 1️⃣ **Cloner le projet**
```sh
git clone https://github.com/vlaine5/plexarr.git
cd plexarr
```

### 2️⃣ **Créer un fichier `.env`**
Copiez l'exemple `.env.example` en `.env` :
```sh
cp .env.example .env
```
Modifiez les valeurs selon votre configuration (notamment votre clé WireGuard pour Gluetun).

### 3️⃣ **Créer le réseau Docker**
Avant de démarrer la stack, assurez-vous que le réseau existe :
```sh
docker network create plexarr
```

### 4️⃣ **Lancer les conteneurs**
```sh
docker-compose up -d
```

---

## ⚙️ **Configuration des services**

### 📺 **Accès aux services**
| Service       | URL par défaut                  | Port externe | Port interne |
|--------------|--------------------------------|--------------|--------------|
| Plex        | `http://NAS_IP:32400/web`      | 32400        | 32400        |
| Sonarr      | `http://NAS_IP:11001`          | 11001        | 8989         |
| Radarr      | `http://NAS_IP:11002`          | 11002        | 7878         |
| Bazarr      | `http://NAS_IP:11005`          | 11005        | 6767         |
| qBittorrent | `http://NAS_IP:11000`          | 11000        | 8080         |
| Prowlarr    | `http://NAS_IP:11006`          | 11006        | 9696         |
| Jackett     | `http://NAS_IP:11007`          | 11007        | 9117         |
| Readarr     | `http://NAS_IP:11008`          | 11008        | 8787         |
| Lidarr      | `http://NAS_IP:11009`          | 11009        | 8686         |
| Tautulli    | `http://NAS_IP:11004`          | 11004        | 8181         |

✍️ **Remarque** : Remplacez `NAS_IP` par l'IP de votre serveur.

### 📡 **Ports requis pour Plex**
| Protocole | Port externe | Port interne | Description |
|-----------|--------------|--------------|-------------|
| UDP       | 1900        | 1900         | Accès au serveur DLNA Plex |
| UDP       | 5353        | 5353         | Ancien système de découverte réseau Bonjour/Avahi |
| TCP       | 8324        | 8324         | Contrôle Plex pour Roku via Plex Companion |
| UDP       | 32410       | 32410        | Découverte réseau GDM |
| UDP       | 32412       | 32412        | Découverte réseau GDM |
| UDP       | 32413       | 32413        | Découverte réseau GDM |
| UDP       | 32414       | 32414        | Découverte réseau GDM |
| TCP       | 32469       | 32469        | Accès au serveur DLNA Plex |

---

## 📜 **Licence**
Ce projet est sous licence MIT.

---

## 📢 **Crédits & Remerciements**
Basé sur les images officielles de **LinuxServer.io** et **Gluetun**.

**Contributeurs** : @vlaine5

---



