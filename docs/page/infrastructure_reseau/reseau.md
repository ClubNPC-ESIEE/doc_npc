## Pfsense
> Pfsense est une basé sur freeBSD (distroLinux).
> C’est un OS à installer sur un ordinateur bidon ou à virtualiser (attention à bien avoir 2 ports Ethernet). 

La configuration est simple pour juste “que ça marche” mais plus on apprend à s'en servir plus on se rend compte à quel point c’est puissant. 

La machine fera office de routeur et de firewall, il fait aussi :     

* DNS
* DHCP 
* User Manager (RADIUS)
* VPN 
* Captive Portal

Et fondamentalement, c’est une distro linux donc tu peux y installer ce que tu veux. 

### Installation
Tu télécharge l’iso pfsense la plus récente ici : [pfsense.org](https://pfsense.org/download/)
tu l’installe directement sur un pc ou tu crée une VM  (cf doc proxmox)

Tu importe le fichier de configuration qui se trouve dans le même dossier que ce doc 

Et ça roule ! 

C’est ça l'intérêt de la pfsense, c’est simple, ça marche bien et c’est polyvalent. 
### Configuration réseau du club
A l’heure ou j’écris cette doc, la pfsense est virtualisée sur un serveur entreposé sous l’escalier de la mezzanine du club 

On a (bientôt) 2 gateway (accès internet):  
WAN ESIEE : permet un accès fibré et rapide (pour avoir un bon débit et pas de latence) mais filtré donc pas de porn ou de serveur host (ils nous trust pas)  
Y’a encore des firewall derrière, en vrai si tu conf mal le firewall c’est pas grave, y’a pas de trafic de toute façon.  
Aussi OPENGATE est censée se fibrer un jour, donc pas sur que cette co reste, mais pour l’instant c’est comme ca ^^

WAN OG : Pas filtrée , mais c’est de la VDSL, donc pas beaucoup de débit (8 mbs).   
Ducoup c’est cool pour host nos conneries mais pour jouer à 15 sur la co c’est moyen…

IP WAN ESIEE : 
...

## Pihole
...

## Switching
...

## ipam
...