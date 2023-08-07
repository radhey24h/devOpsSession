# pull official base image
FROM node:16.4.2-alpine as build

# set working directory
WORKDIR /app

#copy the react app to the container
COPY . /app/

#prepare the container for building react
RUN npm install --silent
#RUN npm install react-scripts@3.0.1 -g --silent
RUN npm run build

# prepare nginx
FROM nginx:1.16.0-alpine
COPY --from=build /app/build /usr/share/nginx/html
#in case if you want to add some permission on copied build folder subfolder we can write below commands
# RUN find /usr/share/nginx/html -type d -exec chmod 755 {} +
# RUN find /usr/share/nginx/html -type f -exec chmod 755 {} +
# RUN find /usr/share/nginx/html -type d -exec chmod +x {} +
RUN rm /etc/nginx/conf.d/default.conf
COPY conf/default.conf /etc/nginx/conf.d

#fire up nginx

EXPOSE 80
EXPOSE 443

CMD ["nginx","-g","daemon off;"]