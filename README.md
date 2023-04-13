# Plexarr Stack


Compose with all you need to be free :) Here is Plexarr stack services and associated ports in the compose : 
- Plex 
	- UDP: 1900 (access to the Plex DLNA Server)
	- UDP: 5353 (older Bonjour/Avahi network discovery)
	- TCP: 8324 (controlling Plex for Roku via Plex Companion)
	- UDP: 32410, 32412, 32413, 32414 (current GDM network discovery)
	- TCP: 32469 (access to the Plex DLNA Server)
- Sonarr
	- Port : 7989
- Radarr
	- 6878
- qBitorrent
	- 7000 (web access)
- flaresolverr
	- 7191
- overseerr
	- 7055
- tautulli
	- 7181
- bazarr
	- 6767
- prowlarr
	- 9696
- readarr
	- 8787
- lidarr
	- 8686

### Prerequisites :
Plex is an host network and Servarr on a user defined bridge.

	Volumes folder creation example : 

```bash
mkdir /seedbox /docker
cd /seedbox
mkdir -p Downloads/InProgress \
Downloads/movies \
Downloads/tv \
comics \
tv \
movies

cd /docker
mkdir -p plex \
qbitorrent/config \
sonarrv3 \
radarr \
overseerr \
tautulli \
bazarr \
prowlarr \
readarr \
audiobookshelf/audiobooks \
lidarr
```

### Installation

1) Install docker and compose on your host

```bash
curl -fsSL https://get.docker.com | sh; >/dev/null
curl -sL "https://github.com/docker/compose/releases/download/v2.17.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

2) Assume all folders are created
3) Clone the repo to get the compose inside your host
4) Then up the compose : 

```bash
cd plexarr
docker-compose up -d
```
