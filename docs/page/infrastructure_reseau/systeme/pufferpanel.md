![Prometheus](https://avatars.githubusercontent.com/u/9778794?s=280&v=4){ align=right width="200" }

PufferPanel est un panneau de gestion de serveurs de jeux en ligne. Il vous permet de gérer plusieurs serveurs de jeux différents depuis un emplacement central. Que vous exécutiez des serveurs Minecraft, Spigot, Source Dedicated Servers, BungeeCord ou d’autres, PufferPanel simplifie la gestion en fournissant une interface web conviviale. Vous pouvez attribuer des serveurs à d’autres utilisateurs, surveiller les performances et effectuer des tâches administratives essentielles. En somme, PufferPanel facilite la gestion de vos serveurs de jeux

### Installation - Docker
On va donc créer un conteneur docker pour installer PufferPanel avec les commandes suivantes : 
```bash
$ mkdir -p /var/lib/pufferpanel
$ docker volume create pufferpanel-config
$ docker create --name pufferpanel -p 8080:8080 -p 5657:5657 -v pufferpanel-config:/etc/pufferpanel -v /var/lib/pufferpanel:/var/lib/pufferpanel -v /var/run/docker.sock:/var/run/docker.sock --restart=on-failure pufferpanel/pufferpanel:latest
$ docker start pufferpanel
```

On va ajouter un joueur pour pouvoir se connecter a l'interface de PufferPanel avec la commande suivante : 
```bash
docker exec -it pufferpanel /pufferpanel/pufferpanel user add
```

Vous aurais donc besoin de rentrer un nom d'utilisateur, un email et un mot de passe pour pouvoir vous connecter a l'interface de PufferPanel qui est a l'adresse `localhost:8080`.

### Utilisation 
Une fois connecter vous aurez donc la possibiliter de créer des serveurs de jeux, de les gérer, de les attribuer a d'autre utilisateur et de voir les performances de vos serveurs. Pour ce faire ...

### Configuration d'un serveur de jeu

***
##### Reférence
[Installing PufferPanel using Docker](https://docs.pufferpanel.com/en/2.x/installing-docker.html)