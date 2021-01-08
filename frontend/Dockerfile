# FROM mhart/alpine-node:15.5.1
FROM node:lts-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install


COPY .eslintrc.js ./
COPY babel.config.js ./

COPY . .

RUN ls
RUN ls ./src

EXPOSE "${PORT:-8080}:80"

CMD ["yarn", "serve"]
