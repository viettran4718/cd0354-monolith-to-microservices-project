### Build
FROM node:14.15 as build
## Create app directory
WORKDIR /usr/src/app

RUN npm i -g ionic
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json package-lock.json ./
RUN npm ci
## Bundle app source
COPY . .
RUN ionic build
### Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=build  /usr/src/app/www /usr/share/nginx/html

# # Stage 1: Build the Angular app
# FROM node:14 as build

# WORKDIR /app

# COPY package.json package-lock.json ./
# RUN npm install --force

# COPY . .
# RUN npm run build

# # Stage 2: Serve the Angular app using NGINX
# FROM nginx:alpine

# COPY --from=build /app/www /usr/share/nginx/html

# EXPOSE 80

# CMD ["nginx", "-g", "daemon off;"]