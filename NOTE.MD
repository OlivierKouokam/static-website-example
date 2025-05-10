Static Website Example - Build MultiStage
-----------------------------------------
 - Dockerfile

> #Premier Stage

> FROM debian:bullseye-20240722-slim as files

> LABEL maintainer='kouokamcarl@gmail.com'

> RUN DEBIAN_FRONTEND=noninteractive apt update && apt install git -y && apt clean -y && rm -Rf /var/lib/apt/lists/*

> RUN mkdir /opt/files

> RUN git clone https://github.com/OlivierKouokam/static-website-example.git /opt/files/

> #Deuxieme Stage

> FROM nginx:alpine3.20-slim

> LABEL maintainer='kouokamcarl@gmail.com'

> ENV PORT=8090

> COPY --from=files /opt/files/ /usr/share/nginx/html/

> COPY nginx.conf /etc/nginx/conf.d/default.conf

> EXPOSE 8090

> CMD sed -i -e 's/$PORT/'"$PORT"'/g' /etc/nginx/conf.d/default.conf && nginx -g 'daemon off;'


 - Commande docker pour builder l'image

    > docker build -t static-webapp:v1 .

 - Commande docker pour démarrer le conteneur

    > docker run --name static-web -p 8080:8090 -d static-webapp:v1

       ou bien

    > docker run --name static-web -p 8080:8080 -e PORT=8080 -d static-webapp:v1
