## Installation pour Raspberry Pi 3

**2.1. Telechargement & Installation de l'image GeoPoppy**

**2.2. Adresses et connexions**

**2.3. Installation manuelle en ligne de commande**

![geo-poppy](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/geopoppy_2.png)


**2.1. Telechargement & Installation de l'image GeoPoppy**

* Télécharger l'image de GeoPoppy sur votre ordinateur(1.8Go):

 https://cartman.sig.inra.fr/geopoppy/GeoPoppy-0_1_5.img.zip

> Ne pas copier directement l'image GeoPoppy sur la carte micro SD !!!

* Télécharger et installer sur votre ordinateur ETCHER (windows, linux, mac), ce programme va permettre de positionner correctement l'image GeoPoppy téléchargée dans la carte micro SD: https://etcher.io/

* Insérer la carte Micro SD dans l'ordinateur 

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRrqS8MhQYdjrRmaYZS-RCtgLIrhB8gdLaxUmAfey96t6YpopQr)

* Démarrer le programme Etcher, choisir l'image telechargee, la carte SD (normalement déjà selectionnée) et flasher la carte

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Dl3GufZWwAIXbet.jpg)

* Sortir la carte SD de l'ordinateur 

* Insérer la carte micro SD dans le Raspberry Pi et mettre sous tension. 
> Il est possible de connecter un écran en HDMI sur le raspberry pour visualiser le déroulement de l'installation. Vous pouvez brancher un cabe Ethernet sur votre réseau pour avoir un accès au web.
Une antenne GPS, clavier ou une clef USB peut egalement être branché.

![](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/3addc4ca2ca0b7c999bdb03a46801a729614b235/en/images/pi-plug-in.gif)



* les leds du raspberry s'allument et/ou clignottent pendant ce premier démarrage (decompression et installation des images logiciel).
Quand l'une d'elle s'éteint deffinitivement (attention à ne pas confondre avec certaines petites coupures) l'installation est fini (env 15-20 min ou plus).

* A la fin de l'initialisation, connecter son smartphone, tablette, pc au réseau wifi GeoPoppy_Pi3 (password : geopoppy)

> Pour les smartphones 3G-4G, penser à couper les data mobiles !!!

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/IMG_20181111_123326_274.jpg)


* Ouvrir un navigateur internet et coller cette adresse pour accéder aux projets demo lizmap:

 https://172.24.1.1  

sur un pc si le raspberry est connecté au réseau par cable ethernet:

 https://geopoppy.local

> connexion ssh : ssh pirate@geopoppy.local

> login: pirate (pour passer Root sudo -s)

> mdp: geopoppy




________________________________________________________________________________

**2.2 Adresses et connexions**

  * Lizmap :
  
    Via navigateur web :  
Il est nécessaire d'ajouter une exception de sécurité lors du premier accès à Lizmap.

        https://172.24.1.1
        login : admin
        mot de passe : admin

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Screenshot_20181111-170717.png)

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Screenshot_20181111-170809.png)

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Screenshot_20181111-171945.png)

  * Postgres/Postgis : 

    Via pgAdmin ou QGIS : 

        ip: 172.24.1.1 
        port: 5432 
        base: geopoppy 
        login et mot de passe: docker
      
  * CloudCommander (permet d'accéder a l'arborescence de fichiers de GeoPoppy et glisser/déposer vos propres fichiers  Qgis et lizmap :

    Via navigateur web :  

        http://172.24.1.1:8000
        login : admin
        mot de passe : admin
        Répertoire: mnt/fs/

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Screenshot_20181111-192246.png)

![](https://raw.githubusercontent.com/jancelin/geo-poppy/master/docs/images/Screenshot_20181111-192922.png)

        
  * Portainer : 

    Via navigateur web :  
    
        http://172.24.1.1:9000
        login : à créer
        mot de passe : à créer

--------------------------

**2.3. Installation manuelle en ligne de commande**

* Insérer la carte Micro SD dans le PC

* télécharger l'OS Hypriot 32bits: http://blog.hypriot.com/downloads/

* Flasher raspbian  sur une Micro SD avec ETCHER: https://etcher.io/
* insèrer la sd dans le raspberry
* connecter l'ethernet (accès web nécessaire)
* brancher
* connection en ssh:

```
ssh pirate@black-pearl.local
```
ou 

```
ssh pirate@"ton ip"
```

> mot de passe : hypriot

```
sudo -s

curl -fsSL https://raw.githubusercontent.com/jancelin/geo-poppy/master/install/auto_install_geopoppy_32bits.sh | sh

```

* chargement des images logiciels  (env 15 min):

* enfin redémarrer le raspberry pour activer le wifi direct et utiliser GeoPoppy

```
sudo reboot
```

