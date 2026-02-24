# 1-Installer-Docker

Nous allons maintenant installer Docker CLI sur notre machine

## Suppréssion des paquets du repos Debian

Avant d'ajouter les paquets qui viennent directement de Docker, nous devons supprimer ceux de Debian en premier

~~~ sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-doc podman-docker containerd runc | cut -f1)
