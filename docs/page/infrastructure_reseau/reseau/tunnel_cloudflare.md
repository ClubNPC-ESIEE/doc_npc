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

!!! danger "Attention"
    La sécurité fournie par Cloudflare et une sécurité qui utilise la méthode du **man-in-the-middle**, c'est-à-dire que Cloudflare va intercepter les requêtes et les réponses entre le client et le serveur.