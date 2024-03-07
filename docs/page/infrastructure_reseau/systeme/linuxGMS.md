![Prometheus](https://marketplace-assets.digitalocean.com/logos/linuxgsm.png){ align=right width="150" }

LinuxGSM (Linux Game Server Managers) est un ensemble de scripts et d’outils conçus pour simplifier la gestion des serveurs de jeux sous Linux. Il facilite l’installation, la configuration et la surveillance des serveurs de jeux, permettant aux administrateurs de passer moins de temps sur la gestion et plus de temps à jouer. C’est un outil open source distribué sous la licence MIT.

### Installation - Docker

#### csgoserver
On va donc faire une installation type avec un serveur pour le jeux CSGO. Pour sa on va utiliser l'installation en docker-compose suivante : 
```yaml
version: '3.4'
services:
  linuxgsm-csgo:
    image: gameservermanagers/gameserver:csgo
    # image: ghcr.io/gameservermanagers/gameserver:csgo
    container_name: csgoserver
    volumes:
      - /path/to/csgoserver:/data
    ports:
      - "27015:27015/tcp"
      - "27015:27015/udp"
      - "27020:27020/udp"
      - "27005:27005/udp"
    restart: unless-stopped
```
Une foi installer vous pouvez faire des commandes dans le docker pour la gestion du serveur de jeux avec : 
```bash
docker exec -it --user linuxgsm csgoserver ./csgoserver details
```

### Utilisation

*** 
##### Reférence
[LinuxGSM Game Server Docker Image](https://hub.docker.com/r/gameservermanagers/gameserver)