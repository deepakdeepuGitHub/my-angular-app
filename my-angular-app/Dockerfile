FROM node:22-alpine AS angular

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

COPY . .

RUN npm run build 

FROM httpd:alpine3.15

WORKDIR /usr/local/apache2/htdocs/

COPY --from=angular /app/dist/my-angular-app/ ./

ExPOSE 80