# Content: Dockerfile for creating a custom image based on the official nginx image
FROM nginx:latest

# Copy the html folder to the nginx html folder
COPY html /usr/share/nginx/html

# Copy the custom configuration file to the nginx configuration folder
ENTRYPOINT ["/docker-entrypoint.sh"]

# Start the nginx server
CMD ["nginx", "-g", "daemon off;"]

## Ref: https://hub.docker.com/r/joaopelisson/nginx-fullcycle