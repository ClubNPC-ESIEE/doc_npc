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
![pihole_logo](https://hobosource.files.wordpress.com/2018/02/pi-hole-logo.png){ align=right width="150" }

Pi-hole est un bloqueur de publicité au niveau du réseau. Il agit comme un DNS menteur et éventuellement comme un serveur Dynamic Host Configuration Protocol (DHCP), destiné à être utilisé sur un réseau privé.

En termes simples, Pi-hole est un outil qui peut bloquer les publicités pour tous les appareils sur votre réseau. Il fonctionne en inspectant les requêtes DNS (Domain Name System) faites par vos appareils et en bloquant celles connues pour héberger des publicités ou même des fichiers malveillants.

Il est capable de bloquer non seulement les publicités traditionnelles sur les sites Web, mais aussi les publicités moins conventionnelles, telles que celles sur les téléviseurs intelligents et les publicités pour systèmes d’exploitation mobiles. - Copilote

### Installation
Pour ça, on va utiliser l'installeur de pihole, qui est un script bash. 
```bash
curl -sSL https://install.pi-hole.net | bash
```
Il va vous demander de choisir votre interface réseau, puis de choisir votre DNS (on va mettre celui de cloudflare). Ensuite, il va vous demander si vous voulez activer le DHCP. Enfin, il va vous donner un mot de passe pour accéder à l'interface web de pihole. Et une fois fini, il vous donnera le lien vers le dashboard de pihole.

### Utilisation 
Une fois connecté, vous allez sur le dash bord de pihole, vous pouvez voir les requêtes DNS qui sont faites sur votre réseau, les bloquer, les autoriser, etc... Rien de bien méchant pour le moment.

#### Configuration pour un appareil
Vous allez dans les réglages de votre appareil, puis dans les paramètres réseau. Vous allez changer le DNS pour mettre l'adresse IP de votre serveur pihole.

#### Configuration pour un réseau
Vous allez dans les paramètres de votre routeur, ensuite dans les paramètres DNS. Vous allez changer le DNS pour mettre l'adresse IP de votre serveur pihole.

### Ajout de listes de blocage
Aller dans la section **Adlist**, Dans **Address** mettez l'adresse de la liste de blocage que vous voulez ajouter. Vous pouvez en trouver sur Internet. Vous pouvez ajouter une description à cette liste dans **Comment**. Puis faite **Add**. Pour actualiser dans la note en dessous dans **Hints**, cliquer sur **online**, après **update**.

## Switching
...

## ipam
...

## Tunnels (Clouflare)
![cloudflare_tunnel](https://cf-assets.www.cloudflare.com/slt3lc6tev37/6yPC24VMmlijkEvr4iIqOl/7f4c0d8aca6f26631751e1a3e8c926a7/tunnel-hero-illustration.svg){ align=right width="300" }

La tunnelisation est une méthode utilisée dans le domaine des réseaux pour transporter des données en utilisant des protocoles qui ne sont pas pris en charge par ce réseau. Cela fonctionne en encapsulant les paquets, c’est-à-dire en enveloppant les paquets dans d’autres paquets. Cette technique est souvent utilisée dans les réseaux privés virtuels (VPN) et peut permettre l’utilisation de protocoles réseau non pris en charge, établir des connexions efficaces et sécurisées entre les réseaux, et dans certains cas, permettre aux utilisateurs de contourner les pare-feu. - Copilote

En ce qui concerne Cloudflare, ils utilisent la tunnelisation pour protéger les propriétés Internet des exploits de vulnérabilité. De plus, la tunnelisation Cloud est utilisée pour éviter le besoin de se déplacer sur les installations déjà déployées pour des tâches telles que des diagnostics, de la maintenance ou de la reconfiguration. Cette technologie permet un accès à distance aux dispositifs du réseau local comme les serveurs, PC, imprimantes, téléphones IP, enregistreurs, caméras, etc..., sans ouverture de ports et sans VPN complexes. - Copilote

* Protection contre les attaques 

    ![illustration1](https://cf-assets.www.cloudflare.com/slt3lc6tev37/5uLXEYIlWL2EyMuugX2H4U/44763f7d73ffa8cdfc206e200bcaa6d1/BDES-1971_Argo-Tunnel-Diagrams_fr-FR.svg)

* Sécurisation des applications internes

    ![illustration2](https://cf-assets.www.cloudflare.com/slt3lc6tev37/7L1lRILL53vxEoPzYfgZz8/ae0e13b872f1204aa3f0ec9a9c3322b1/BDES-1971_Cloudflare_Diagrams_Web_fr-FR.svg)

*[Cloudflare - tunnel](https://www.cloudflare.com/fr-fr/products/tunnel/)*

### Créer un compte Cloudflare
Rendez-vous sur le site de [Cloudflare](https://www.cloudflare.com) et créez un compte. Une fois cette étape faite, vous pouvez vous connecter à votre compte et accéder à votre tableau de bord *([dash](https://dash.cloudflare.com))*. 

!!! warning "Attention"
    Quand vous créez votre compte, vous pouvez choisir une offre gratuite ou payante ; pour le moment, nous allons utiliser l'offre gratuite. Ils vont vous demander de rentrer un moyen de paiement, mais vous ne serez pas débité. *(Si vous ne le faites pas, le tunnel ne va marcher qu'en local et pas depuis Internet :) )*

### Ajouter un Domaine
Pour ajouter un domaine, allez sur la zone **Websites**, puis cliquez sur **Add a site** suivez les indications demandées et vous pourrez ajouter votre domaine.

### Nameservers
Vous allez sûrement avoir une erreur qui vous dit que votre domaine n'est pas encore disponible et utilisable par Cloudflare. Pour cela, vous allez devoir aller dans la section **DNS** puis **Records**. Une fois dans cette section, vous aurez donc en bas de la page les **Nameservers** (2 normalement). Vous allez ensuite vous rendre dans votre gestionnaire de domaine (OVH, GoDaddy, etc...) et vous allez remplacer les **Nameservers** par ceux de Cloudflare dans la zone serveur DNS de votre domaine.

### Télécharger le client Cloudflared
Pour cela, on va donc suivre les indications de Cloudflare. Sur le tableau de bord de votre compte Cloudflare, allez sur la section **Zero Trust**, puis dans **Networks** et enfin **Tunnels**. Choisissez **Cloudflared**, ensuite donnez un nom à votre tunnel. Enfin, il vous proposera diverses installations selon votre OS pour l'installation du client Cloudflared. Une fois l'installation terminée et bien réalisée, le serveur que vous avez connecté devrait apparaître dans **Connnector**. Si tout est bon, alors votre tunnel est bien connecté.

### Ajouter une application au tunnel
Dans **Add Public hostname**, choisissez votre **Subdomain** (nom de l'app par exemple) et dans **Domain** le domaine connecté et activé à votre compte. Dans **Type** mettez le style d'application que vous voulez connecter (HTTP, HTTPS, TCP, etc...). Enfin, dans **URL** mettez l'adresse IP de votre serveur local.

Si tout se passe bien, vous devriez avoir une application connectée à votre tunnel et votre tunnel qui vous indique **Healthy** en status. 

### Ajouter une sécurisation à une de vos applications avec **Access**
Ici, on va ajouter une sécurité à une des applications qu'on a ajoutées au tunnel. Dans le cas ici, on a des applications **Self-hosted** c'est donc cette option qu'on va choisir. 

Donnez-lui un nom et la durée de validation de la connexion. Remettez le **Subdomain** et **Domain** comme précédemment. 

*(personnellement, je désactive **Application Appearance**)*. 

Faites **next**, donnez un nom à votre **Policy**. Ici, on va créer une authentification par mail, ainsi, on va choisir **Email** dans **Configure rules** et dans **value**, on va mettre tous les mails autorisés.

Faites **next**, et enfin **add application**. 