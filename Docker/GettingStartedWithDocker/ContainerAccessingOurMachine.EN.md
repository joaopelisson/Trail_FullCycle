# Accessing Docker Host Resources from a Container

When running a container, you might need to access a port or resource on the host machine where Docker is running. Follow these steps:

1. First, start an interactive container:

   ```bash
   docker run --rm -it --name ubuntu ubuntu bash
   ```

2. Inside the container, it’s recommended to update the system and install `curl`:

   ```bash
   apt-get update
   apt-get install curl -y
   ```

3. Now, suppose the resource you want to access is available on port 8000 of the host (localhost:8000). You can do this by running:

   ```bash
   curl http://host.docker.internal:8000
   ```

And that's it! Your container can now access resources directly from the host machine.
