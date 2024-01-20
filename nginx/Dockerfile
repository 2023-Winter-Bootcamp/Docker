FROM node:13.12.0-alpine as builder
WORKDIR /frontend
COPY ../.env .
COPY ../Frontend/2023winterbootcamp .
RUN npm i && npm cache clear --force && npm run build

FROM nginx
COPY --from=builder /frontend/build /var/www/frontend
RUN rm /etc/nginx/nginx.conf
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf