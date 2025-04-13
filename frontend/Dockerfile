FROM node:18 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine

# Remove default nginx website
RUN rm -rf /usr/share/nginx/html/*

COPY --from=build /app/build /usr/share/nginx/html

# Copy your custom NGINX config
COPY ../nginx/app-nginx.conf /etc/nginx/conf.d/default.conf
