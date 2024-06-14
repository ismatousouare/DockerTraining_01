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
## Recuperer une image
```
docker run --name container_name -it nom_image:tag_image {CMD -optionnelle}
```
## Lister les containers docker en exécution
```
docker ps
```
## Lister tous les containers docker(en exécution et en arrêt)
```
docker ps -a
```
-Supprimer un container
```
docker rm container_name__Or__container_id
```
-Supprimer un container en force
```
docker rm -f container_name__Or__container_id
```
## Creer des images docker avec le fichier Dockerfile
Dans ce exemple nous allons le faire à partir de l'image debian 12.5
```
FROM debian:12.5
```
- Construction de l'image
```
docker build -t image_name:tag_image chemin ou se trouve le dockerfile
```
-Exemple:
```
 docker build -t firstimage:v01 .
```
-Demarrer l'image qui a été créer
```
docker run -it firstimage:v01 sh
```
-Installation de python3 dans l'image
```
RUN apt-get update && apt-get install -y python3
```
## Docker compose
### Installation 
Docker compose est installé en tant que plugin docker
```
services:
  site-1:
    image:  ubuntu/apache2:2.4-21.10_edge
    container_name: site1
    ports:
      -8081:80
```
* Demarrer les services 
```
docker compose up -d
```
# Apache2 sans docker
## Installation
```
sudo apt-get update
sudo apt-get install apache2
```
## Validation de l'installation
```
sudo service apache2 status
```

# Notes
- docker-compose qui la v1 est en python
- docker compose est la v2 de docker compos een golang
- docker compose est un outil qui permet de deployer des conteneurs avec des fichiers de configuration et developpéen open source
# Refernces
-https://docs.docker.com/engine/install/ubuntu/