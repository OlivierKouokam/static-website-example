Static Website Example - Build MultiStage
-----------------------------------------
 - Consulter le Dockerfile pour voir la construction du build multistage

 - Commande docker pour builder l'image

    >> docker build -t static-webapp:v1 .

 - Commande docker pour démarrer le conteneur

    >> docker run --name static-web -p 8080:8090 -d static-webapp:v1

       ou bien

    >> docker run --name static-web -p 8080:8080 -e PORT=8080 -d static-webapp:v1
