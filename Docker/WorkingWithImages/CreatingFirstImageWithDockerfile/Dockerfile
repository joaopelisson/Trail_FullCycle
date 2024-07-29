# Whenever we create an image with a Dockerfile, the first line must be the base image we are going to use
FROM nginx:latest

# The MAINTAINER instruction sets the Author field of the generated images
WORKDIR /app

# Updating the package repository, installing vim, and clearing the cache in a single RUN statement
RUN apt-get update && \
    apt-get install vim -y && \
    apt-get clean

# The COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>
COPY index.html /usr/share/nginx/html/