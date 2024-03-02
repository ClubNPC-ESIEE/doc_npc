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