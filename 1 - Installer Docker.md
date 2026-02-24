# 1-Installer-Docker

Nous allons maintenant installer Docker CLI sur notre machine

## Suppréssion des paquets du repos Debian

Avant d'ajouter les paquets qui viennent directement de Docker, nous devons supprimer ceux de Debian en premier

```bash
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-doc podman-docker containerd runc | cut -f1)
```

## Mise en route du repo Docker

Nous allons d'abord installer les prérequis pour configurer le dépôt.

```bash
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

Nous allons maintenant mettre le repo en place

```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/debian
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

Installation des paquets

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Démarrage de docker

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Et voila docker est installé