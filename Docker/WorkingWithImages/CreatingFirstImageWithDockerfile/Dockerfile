# Whenever we create an image with a Dockerfile, the first line must be the base image we are going to use
FROM nginx:latest

# Updating the package repository, installing vim, and clearing the cache in a single RUN statement
RUN apt-get update && apt-get install vim -y && apt-get clean