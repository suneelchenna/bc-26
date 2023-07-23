#FROM node:12.22.9-alpine as build

#FROM node:14.5.0-alpine as build

FROM node:12.18.3 as build 

WORKDIR /app

#ENV NODE_ENV development

COPY package.json ./

#RUN npm install

RUN npm install

#RUN npm install webpack -g

RUN npm run build

FROM nginx:1.21-alpine

RUN rm -rf /usr/share/nginx/html/*


COPY --from=build /app/dist /usr/share/nginx/html


COPY nginx.conf /etc/nginx/conf.d/default.conf


EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]