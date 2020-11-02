# build stage
FROM node:12-slim as build-stage

WORKDIR /app/
COPY package.json /app/

RUN yarn install
COPY . /app/

RUN yarn build

# production stage
FROM nginx:1.15.8 as production-stage

RUN rm /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx/

RUN rm /etc/nginx/conf.d/default.conf
COPY project.conf /etc/nginx/conf.d/

COPY --from=build-stage /app/dist/ /var/www/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]