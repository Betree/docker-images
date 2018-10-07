# Description
# ===========
# A CentOS image with nginx + node installed
# Also contains node-sass npm package
#
# Configuration
# =============
# Nginx configuration must be put in /etc/nginx/nginx.conf
# To start the server as a blocking process, you must call:
# > nginx -g "daemon off;"
#-----------------------------------------------------------------

FROM centos:latest

# Install node + npm + git
RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash && \
    yum -y install nodejs git

# Install Nginx
RUN yum install -y epel-release && yum install -y nginx

# Install node-sass
RUN npm install -g node-sass npx
