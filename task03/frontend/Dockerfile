FROM node:12-alpine as build
WORKDIR /app
COPY package.json .
RUN npm install
COPY . /app
RUN npm run build
FROM nginx:1.16.0-alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY config/default.conf /etc/nginx/conf.d/default.conf
