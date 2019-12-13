# Projet_interco
Repo Git pour le projet d'interconnexion réseau ASR

Dans le dossier Docker_File_Deja_Fait, il y a des exemple de dockerfiles pour lancer des dockers qui serviront à lancer des routeurs (dossier quagga), serveurs web, ftp ... Je les ai récupérer du projet réseau de l'année
dernière, ils utilisaient ses dockers files pour lancer les différentes machines. Du coup c'est de la frappe. 
Explication d'un des dockers files (en commentaire //) exemple d'un routeur :

FROM debian:jessie-slim // Chargement d'un os, ici debian, à changer selon ce que vous voulez
RUN apt-get update // Update de l'apt-get du docker
RUN apt-get -y install iptables apt-utils iproute2 net-tools systemd telnet nano iputils-ping tcpdump inetutils-traceroute quagga // Ici on installe tous ces paquets dès la construction du docker
RUN apt-get -f install // Jsp
COPY  ./quagga /etc/quagga // On copie dans notre docker le dossier quagga qui contient les démons de routage dans le dossier etc du docker.
RUN mkdir /etc/scripts  // On créer un dossier qui servira pour les scripts
ENV PATH "/etc/scripts:$PATH" 
ENTRYPOINT /etc/init.d/quagga start && /bin/bash // Lancement de quagga. 

PS : Justin est vraiment bg
