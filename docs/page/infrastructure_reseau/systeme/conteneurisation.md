*Prérequis : [Virtualisation](./virtualisation.md)*

> Expliquer la conteneurisation sans avoir compris la virtualisation, c’est compliqué donc lis la [doc précédente](./virtualisation.md). 

Pour comprendre la conteneurisation, on va la comparer avec la virtualisation :
![Conteneurisation](../../../img/systeme/docker.png)

Comme vu précédemment, la virtualisation va host plusieurs OS, et leurs binaires/librairies séparément ce qui apporte plein d’avantages.

Les conteneurs fonctionnent un poil différemment.   
L’objectif est le même : cloisonner   
Seulement, on ne le fait pas au niveau de l’OS, en effet l’OS reste le même, ou plus précisément le kernel de l’OS. En faisant cela, on a une application qui tourne dans un environnement effectivement différent, mais qui utilise le même kernel (gain de place en disque notamment), mais la surcouche OS change et  les bibliothèques/binaires aussi.  

Ca apporte les mêmes avantages que la virtualisation, à 2 différences près : 

- C’est plus léger, car tu partage le kernel
- C’est moins safe, car tu partage le kernel

Proxmox propose des conteneurs  LXC (linux), qui fonctionnent exactement comme des VM d’un point de vue extérieur, mais il y a un type de conteneurs encore plus intéressant (bien que basé sur LXC), les dockers. 

### Commentcamarche :  

- Tu crée une VM/CT linux quelconque
- `sudo apt update && apt upgrade -y` (la classique)
- Tu installe le docker ! (google est ton ami lol amuse toi bien) *(Tu peux soit utiliser apt mais c’est pas toujours stable soit passer par les installer officiels via wget ou curl, dans tous les cas ca marche)*  
    Youhou t’as installé docker, maintenant 2 choix s’offrent à toi :   
    __La voie des faibles (bien pour comprendre au début) :__  

    - Tu utilise une image docker de quelqu’un d’autre sur Docker Hub
        - `sudo docker pull helloworld`
        - `sudo docker run helloworld`  
    
    __La voie des braves : Crée ton image docker__  

    - Tu décris ce que tu veux faire dans un `dockerfile`   
    	- De quoi tu pars (Une alpine (distro linux ultra légère) ou une ubuntu, c’est pas la même à l’usage)  
    	- Toutes les commandes pour installer / faire ce que tu veux  
		- La conf réseau que tu veux   
		- Les volumes que tu veux utiliser etc… 