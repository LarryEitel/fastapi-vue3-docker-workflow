FROM node:latest as build-stage
WORKDIR /app
COPY frontend/package*.json ./
RUN ls -l
RUN npm install
COPY frontend/ .
RUN ls -l
RUN npm run build

FROM nginx as production-stage
RUN mkdir /app
COPY --from=build-stage /app/dist /app
COPY nginx.conf /etc/nginx/nginx.conf
