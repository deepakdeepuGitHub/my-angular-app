# Stage 1: Build the Angular app
FROM node:22-alpine AS angular

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve the app using Apache HTTP Server
FROM httpd:alpine3.15

# Copy built browser files directly into Apache's public directory
COPY --from=angular /app/dist/my-angular-app/browser/ /usr/local/apache2/htdocs/

EXPOSE 80