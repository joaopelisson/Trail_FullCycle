# Introduction to Docker 🐋

- What are Containers

- How Containers Work

- How Docker Works

- Main Docker Commands

- Dockerfile

- Working with Docker Images

---

### What are Containers?

Containers are a standard unit of software that packages up code and its dependencies, so the application runs quickly and reliably from one computing environment to another.

---

### How do Containers Work?

#### The first point when we talk about containers is processes and `namespaces` that isolate these processes, working in the operating system as follows:

| Namespaces                                                           |
|----------------------------------------------------------------------|
| &nbsp;Operating system                                               |
| &nbsp;&nbsp;Parent process Container 1                               |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Child process container 1  |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Child process container 2  |

Once we kill the parent process, all child processes are killed together.

In other words, `namespaces` = Process Isolation.

#### Cgroups

The idea of CGroups is to isolate the computational resources of this process, so as not to harm others.

It's not enough to just isolate processes; we need to isolate their resources as well, so they don't negatively impact other resources on "our machine".

`Cgroups` = Resource Control

### File System

The idea is to work with layers.

`File System` = OFS (Overlay File System)

#### Images

The image is where the structure is loaded, everything necessary for it to function.

Working with dependency layers.

_Example:_ `myAppImage:v1`

#### Dockerfile

A declarative file where we write how the image we will use will be, that is, we use it to build images!

```
FROM: ImageName
RUN: commands e.g., apt-get install
EXPOSE: 8000
```


In other words...

`myDockerFile` -> build -> `myImage`

The Dockerfile generates the `Build`. When the build is generated, a new image is created.

Another way to generate images is:

`myImage` -> commit -> `myImage:v2`

I take a running container, write to the `Write` layer, and when I commit, a new image is generated.

#### Where are the images stored?

They are stored in the `Image registry`.

| IMAGE REGISTRY |
|----------------|
| IMAGE N        |
| IMAGE Y        |
| IMAGE X        |

Every time I generate a new image from the Dockerfile, this imageName is coming from an `image registry` (i.e., it is doing a `pull`).

However, when I generate the build of this image, I can do a `push`. Once I do a `push`, I am uploading it to my `image registry`.

---

### How Docker Works?

<img src="./How docker works.png" alt="How Docker works" />

