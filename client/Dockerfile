FROM node:alpine AS build
WORKDIR '/app'
COPY package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx:alpine
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/config.d/default.conf
COPY --from=build /app/build usr/share/nginx/html
