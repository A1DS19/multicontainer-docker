FROM node:23-alpine AS build

EXPOSE 3000

WORKDIR /app

COPY package.json /app
COPY package-lock.json /app
RUN npm install

COPY ./ ./

RUN npm run build

FROM nginx:1.27.2
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html