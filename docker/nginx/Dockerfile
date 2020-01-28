FROM ubuntu:18.04
#LABEL project="Nginx Web Server Image"
LABEL maintainer "hitjethva@gmail.com"
RUN \apt-get update && \
apt-get install -y nginx && \
rm -rf /var/lib/apt/lists/* && \
echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
chown -R www-data:www-data /var/lib/nginx
# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]
# Define working directory.WORKDIR /etc/nginx
# Define default command.CMD ["nginx"]
# Expose ports.
EXPOSE 80
EXPOSE 443

# add nginx conf
ADD config/api.keptey.in /etc/nginx/sites-available/api
ADD config/devapi.keptey.in /etc/nginx/sites-available/devapi
ADD config/stageapi.keptey.in /etc/nginx/sites-available/stageapi

# create symlinks 
RUN ln -s /etc/nginx/sites-available/api /etc/nginx/sites-enabled/
RUN ln -s /etc/nginx/sites-available/devapi /etc/nginx/sites-enabled/
RUN ln -s /etc/nginx/sites-available/stageapi /etc/nginx/sites-enabled/


# add nginx conf
#ADD conf.d/default.conf /etc/nginx/conf.d/default.conf

WORKDIR /etc/nginx

CMD ["nginx"]