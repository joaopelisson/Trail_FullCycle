# Working with Docker Networks

To manage networks in Docker, the primary command you need to know is `docker network`. It offers various options for creating, listing, inspecting, and removing networks, allowing you to configure and control how your containers communicate.

### Listing Available Networks

A good starting point is to check the networks that are already configured in Docker. To do this, use:

```bash
docker network ls
```

This command displays all the available networks, showing which ones are ready for use. A typical output might look like this:

```bash
NETWORK ID     NAME      DRIVER    SCOPE
a1f44ec5cd9d   bridge    bridge    local
4cf449d96503   host      host      local
4891632868g4   none      null      local
```

### Understanding the Default Network

By default, when you create a container without specifying a network, Docker automatically connects it to the `bridge` network. This is the default network, used in most cases.

To view the details of the `bridge` network, you can use the following command:

```bash
docker network inspect bridge
```

### Creating Your Own Network

If you need a custom network, you can create one with the following command:

```bash
docker network create --driver bridge mynetwork
```

After creating the network, run `docker network ls` again, and you’ll see something like this:

```bash
NETWORK ID     NAME        DRIVER    SCOPE
...
4255db102e41   mynetwork   bridge    local
...
```

Your new `mynetwork` is now set up and ready to use.

### Connecting Containers to the Network

In addition to creating networks, you can connect an existing container to a specific network. To do this, use:

```bash
docker network connect mynetwork containerName
```

Now, if you run:

```bash
docker network inspect mynetwork
```

You’ll see more details about the container's connection to the `mynetwork`, allowing you to better manage communication between your containers.