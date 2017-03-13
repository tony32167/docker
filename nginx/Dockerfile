#
# Nginx Dockerfile
#
# https://github.com/dockerfile/nginx
#

# Pull base image.
FROM centos:latest

# Install Nginx.
COPY nginx-release-centos-7-0.el7.ngx.noarch.rpm nginx-release-centos-7-0.el7.ngx.noarch.rpm
RUN rpm -ivh nginx-release-centos-7-0.el7.ngx.noarch.rpm
RUN \
  yum -y update && \
  yum install -y nginx  && \
  useradd www-data && \
#  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /usr/sbin/nginx 

COPY default.conf /etc/nginx/conf.d/default.conf

# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["nginx", "-g", "daemon off;"]

# Expose ports.
EXPOSE 80
EXPOSE 443
