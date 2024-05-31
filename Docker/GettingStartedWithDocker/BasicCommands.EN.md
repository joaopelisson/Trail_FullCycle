# Basic Commands

- `docker run {name}`: Executes the image.

- `docker ps`: Lists running containers.

- `docker ps -a`: Lists all containers, including those that have stopped.

- `-i`: Interactive mode.
- `-t`: TTY - Allows input in the terminal. Typically used together as `-it`.

Example: `docker run -it --rm ubuntu bash`

- `--rm`: Automatically removes the container once it exits.
