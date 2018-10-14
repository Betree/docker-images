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

# Install repos
RUN yum install -y epel-release
RUN curl --silent --location https://rpm.nodesource.com/setup_10.x | bash

# Install Nginx, nodejs and git
RUN yum install -y nginx nodejs git
