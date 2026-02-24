# 1-Installer-Docker

Nous allons maintenant installer Docker CLI sur notre machine

## Suppréssion des paquets du repos Debian

Avant d'ajouter les paquets qui viennent directement de Docker, nous devons supprimer ceux de Debian en premier

``` sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-doc podman-docker containerd runc | cut -f1) ```

## Mise en route du repo Docker

Nous allons avant installer les prérequis pour mettre le repo

``` sudo apt update```
```sudo apt install ca-certificates curl```
```sudo install -m 0755 -d /etc/apt/keyrings```
```sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc```
```sudo chmod a+r /etc/apt/keyrings/docker.asc```