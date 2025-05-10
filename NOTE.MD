Static Website Example - Build MultiStage
-----------------------------------------

docker build -t static-webapp:v1 .

docker run --name static-web -p 8080:8090 -d static-webapp:v1
ou bien
docker run --name static-web -p 8080:8080 -e PORT=8080 -d static-webapp:v1
