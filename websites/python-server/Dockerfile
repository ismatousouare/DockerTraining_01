#base sur l'image python:3.12.3-alpine3.19
FROM python:3.12.3-alpine3.19 
#port sur lequel est exposé l'image
EXPOSE 8081 
#Volume
VOLUME [ "/data_python" ]

#Copy la source vers le dossier su lequel je travaille le . c'est tous les fichier et webapp dans le dossier 
COPY . /webapp/
#On aurait pu aussi faire COPY . . copier tous les fichier sur l'endroit ou je suis donc webapp
#Exemple: ici on aura testapp qui va etre cree puis a l'interieur de lui on aura le dossier test mais avec workir /webapp comme racine par defaut après le build
#WORKDIR /testapp
#RUN mkdir test
#se rendre dans un dossier donc ici lorsque l'on rebuild l'image on se placera sur le dossier webapp par defaut
#Ici webapp représente mon espace de travail
WORKDIR /webapp
CMD python -m http.server 8081

