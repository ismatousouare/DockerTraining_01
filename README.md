# DockerTraining_01
Ceci est une introduction à Docker avec server apache et serveur python
## Installation
### Script
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```
### Validation de l'installation
```
sudo docker version
```
### Ajouter l'utilisateur dans le groupe docker si c'est pas le cas
```
Sudo usermod -aG docker $USER 
```
NB: Apres l'ajout on redemarrer la machine
## Commande de base de docker
- Liste les images
```
docker images
```
-
# Notes
- docker-compose qui la v1 est en python
- docker compose est la v2 de docker compos een golang
- docker compose est un outil qui permet de deployer des conteneurs avec des fichiers de configuration et developpéen open source
# Refernces
-https://docs.docker.com/engine/install/ubuntu/