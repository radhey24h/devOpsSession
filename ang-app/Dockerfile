# pull official base image
FROM node:18.10-alpine as build

# set working directory
WORKDIR /app
#
RUN npm cache clean --force
#copy the react app to the container
COPY . /app/

#prepare the container for building react
RUN npm install --silent
RUN npm install -g @angular/cli --silent

#in case if we want to send a parameter and build on the basis of parameter we can use below command and we have to setup it in package json
ARG envName
ENV env_name=$envName
RUN echo "The env_name is ${env_name}"
RUN npm run build:${env_name}

# without variable name
#RUN npm run build 

# prepare nginx
FROM nginx:1.16.0-alpine
COPY --from=build /app/dist/ang-app /usr/share/nginx/html
#in case if you want to add some permission on copied build folder subfolder we can write below commands
RUN find /usr/share/nginx/html -type d -exec chmod 755 {} +
RUN find /usr/share/nginx/html -type f -exec chmod 755 {} +
RUN find /usr/share/nginx/html -type d -exec chmod +x {} +

RUN rm /etc/nginx/conf.d/default.conf
COPY conf/default.conf /etc/nginx/conf.d

#fire up nginx

EXPOSE 80
EXPOSE 443

CMD ["nginx","-g","daemon off;"]