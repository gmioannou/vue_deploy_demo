# build stage
FROM node:14 as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# production stage
FROM ubuntu:18.04  as production-stage

RUN apt update -y \
    && apt install nginx -y \
    && apt install vim -y \
    && apt-get install software-properties-common -y \
    && add-apt-repository ppa:certbot/certbot -y \
    && apt-get update -y \
    && apt-get install python-certbot-nginx -y \
    && apt-get clean

COPY --from=build-stage /app/dist /usr/share/nginx/html

STOPSIGNAL SIGTERM
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
