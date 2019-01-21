**9. Docker c'est quoi ?**

Comme dit précédemment, ce projet tourne sous Docker. Il est donc nécessaire de comprendre un minimum le fonctionnement des Images, des Containers et de l'Hôte pour bien évoluer dans la gestion de son Raspberry:

https://www.docker.com/

Voici une vue du fonctionnement de Docker, comparé à un système de virtualisation :

![docker_vs_virtualisation](http://www.google.fr/url?source=imglanding&ct=img&q=http://patg.net/assets/container_vs_vm.jpg&sa=X&ei=8EVTVeXcMsuuUffYgMAC&ved=0CAkQ8wc4Ig&usg=AFQjCNGK8s4aWhh1RO28RIJUKRjTvVBlWw)

Par exemple voici l'architecture d'un serveur complet sous Docker:

Nous pouvons voir que notre hôte héberge quelques services, Docker et les fichiers de données persistantes (vos données en résumé).
L'ensemble des applications est "containerisé", permettant une souplesse, une facilité et une rapidité d'installation. Et si c'est cassé, ce n'est pas grave, on reconstruit avec 2 lignes de commandes.

> Exemple d'une installation sous serveur:

![docker_lizmap](https://cloud.githubusercontent.com/assets/6421175/7345474/3f403ca0-ecd5-11e4-8675-714fb9388863.jpg)

> L'installation sur le raspberry ne comprendra que deux images et deux containers (rpi_docker_postgis et docker rpi_docker_lizmap):

![docker_poppy] (https://cloud.githubusercontent.com/assets/6421175/7859796/20f8ecec-0544-11e5-8b46-28125b8de72c.png)
____________________________________________________________________

**Commandes essentielles de Docker**

* ```docker pull jancelin/docker-lizmap``` --> construit l'image venant de dockerhub.
* ```docker build -t jancelin/docker-lizmap git://github.com/jancelin/docker-lizmap ```--> construit l'image via mon dépôt github, permet de voir toute l'installation.
* ```docker images``` --> voir les images disponible dans son docker
* ```docker rmi name_of_image --> supprime l'image```.
* ```docker run --restart="always" --name "websig-lizmap" -p 8081:80 -d -t -v /your_qgis_folder:/home:ro -v /your_config_folder:/home2 jancelin/docker-lizmap ```--> démarre lizmap container
* ```docker ps -a ```--> liste des container et status.
* ```docker start name_container``` --> démarre container.
* ```docker stop name_container``` --> arrête container.
* ```docker rm name_container``` --> supprime le container (possibilité de: docker stop name_container && docker rm name_container)
* ```docker exec -it name_container bash ```--> rentre dans le container avec une session root shell.
* ```docker cp name_container:/file/path/within/container /host/path/target``` ---> copie des fichier du container vers l'hôte. 
* ```docker exec -i moncontainer /bin/bash -c 'cat > /inside-container-file' < fichier-exterieur``` ---> copie des fichiers de l'hôte vers le container 
* ```docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)``` ---> arrête et supprime tous les containers
* ```docker stats `docker ps | awk '{print $NF}' | grep -v NAMES```` ---> voir les stats des containers
* .... ---> https://docs.docker.com/userguide/ 

**Docker-compose**

```
Define and run multi-container applications with Docker.

Usage:
  docker-compose [-f=<arg>...] [options] [COMMAND] [ARGS...]
  docker-compose -h|--help

Options:
  -f, --file FILE             Specify an alternate compose file (default: docker-compose.yml)
  -p, --project-name NAME     Specify an alternate project name (default: directory name)
  --verbose                   Show more output
  -v, --version               Print version and exit
  -H, --host HOST             Daemon socket to connect to

  --tls                       Use TLS; implied by --tlsverify
  --tlscacert CA_PATH         Trust certs signed only by this CA
  --tlscert CLIENT_CERT_PATH  Path to TLS certificate file
  --tlskey TLS_KEY_PATH       Path to TLS key file
  --tlsverify                 Use TLS and verify the remote
  --skip-hostname-check       Don't check the daemon's hostname against the name specified
                              in the client certificate (for example if your docker host
                              is an IP address)

Commands:
  build              Build or rebuild services
  config             Validate and view the compose file
  create             Create services
  down               Stop and remove containers, networks, images, and volumes
  events             Receive real time events from containers
  help               Get help on a command
  kill               Kill containers
  logs               View output from containers
  pause              Pause services
  port               Print the public port for a port binding
  ps                 List containers
  pull               Pulls service images
  restart            Restart services
  rm                 Remove stopped containers
  run                Run a one-off command
  scale              Set number of containers for a service
  start              Start services
  stop               Stop services
  unpause            Unpause services
  up                 Create and start containers
  version            Show the Docker-Compose version information
```
source: https://docs.docker.com/compose/reference/overview/