# build environment
FROM node:15.5.1-alpine as build
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH

# COPY package.json /app/package.json
COPY package.json ./

RUN npm install --silent
RUN npm install @vue/cli@4.5.8 -g

COPY .eslintrc.js ./
COPY babel.config.js ./
COPY . .

RUN npm run build

# production environment
FROM nginx:1.19.6-alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
