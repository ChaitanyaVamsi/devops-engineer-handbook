

---

# DAY 2: Docker – Complete Interview Notes

---

# 1. What is Docker?

Docker is a containerization platform that allows you to package an application with all its dependencies and run it anywhere consistently.

---

# 2. Image vs Container

## Image

An image is a read-only template that contains:

* Base OS (minimal OS)
* System packages
* Application runtime (Java, Python, Node, etc.)
* Application code
* Dependencies

Image = Blueprint

---

## Container

A container is a running instance of an image.

Image + Running State = Container

You can create multiple containers from the same image.

---

# 3. Basic Docker Commands

## List Containers

```bash
docker ps        # Running containers
docker ps -a     # All containers (running + stopped)
```

## List Images

```bash
docker images
```

---

# 4. Pulling Images

```bash
docker pull <image-name>:<tag>
```

Example:

```bash
docker pull nginx:latest
```

If the image is not available locally, Docker pulls it from Docker Hub.

---

# 5. Creating and Starting Containers

## Step by Step

```bash
docker create <imageID>
docker start <containerID>
```

## One-line Command

```bash
docker run = pull + create + start
```

Example:

```bash
docker run -d nginx
```

---

# 6. Port Mapping

```bash
docker run -d -p <host-port>:<container-port> nginx
```

Example:

```bash
docker run -d -p 80:80 nginx
```

Access via:

```
http://<public-ip>
```

Example:

```
http://98.92.17.244
```

---

# 7. Running Container in Background

```bash
docker run -d nginx
```

`-d` runs the container in detached mode (background).

---

# 8. Access Inside a Container

```bash
docker exec -it <container-id> bash
```

---

# 9. Inspect Image or Container

```bash
docker inspect <image/containerID>
```

---

# 10. Remove All Containers

```bash
docker rm -f $(docker ps -a -q)
```

---

# 11. Dockerfile

A Dockerfile is a text file containing instructions to build custom Docker images.

---

# 12. Important Dockerfile Instructions

## FROM

* Defines base image.
* Must be the first instruction.

```dockerfile
FROM almalinux:9
```

---

## RUN

* Executes during image build time.
* Used to install packages and configure image.

Example:

```dockerfile
RUN dnf install nginx -y
```

You can have multiple RUN instructions.

---

## CMD

* Executes when container starts.
* Only one CMD should be used (last one is considered).

Example:

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

Important:

* CMD must run in foreground.
* If the CMD process stops, the container stops.

Incorrect example:

```dockerfile
CMD ["systemctl", "start", "nginx"]
```

Why?

Containers do not run full init systems like systemd by default.

---

## LABEL

Adds metadata to the image.

```dockerfile
LABEL author="Ramesh"
```

Used for filtering and documentation.

---

## EXPOSE

Provides information about ports used by container.

```dockerfile
EXPOSE 80
```

It does not open the port. It is only documentation.

---

# 13. Build Custom Image

```bash
docker build -t <image-name>:<version> .
```

Example:

```bash
docker build -t myapp:v1 .
```

`.` means Dockerfile is in the current directory.

---

## Build Without Cache

```bash
docker build --no-cache --progress=plain -t run:v1 .
```

---

# 14. Docker Hub – Push & Pull

## Login

```bash
docker login
```

---

## Tag Image

```bash
docker tag image-name:version username/image-name:version
```

Example:

```bash
docker tag myapp:v1 ramesh/myapp:v1
```

---

## Push Image

```bash
docker push username/image-name:version
```

Example:

```bash
docker push ramesh/myapp:v1
```

---

## Pull From Custom Registry

Example:

```
docker.io/joindevops/from:version
```

---

# 15. Docker Installation (RHEL / Amazon Linux)

```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user
```

---

# 16. Docker Storage Location

Default Docker directory:

```
/var/lib/docker
```

---

# 17. Disk Extension for Docker (If /var Full)

```bash
growpart /dev/nvme0n1 4
lvextend -L +30G /dev/mapper/RootVG-varVol
xfs_growfs /var
```

Used when Docker storage runs out of space.

---

# Important Interview Differences

## RUN vs CMD

| RUN                          | CMD                             |
| ---------------------------- | ------------------------------- |
| Executes during image build  | Executes during container start |
| Used for installing packages | Used to start application       |
| Multiple allowed             | Only one effective              |

---

## Image vs Container

| Image     | Container              |
| --------- | ---------------------- |
| Blueprint | Running instance       |
| Read-only | Read-write layer added |
| Static    | Dynamic                |

---

# Frequently Asked Interview Questions

## 1. What happens when you run `docker run nginx`?

* Checks locally for image
* If not found, pulls from Docker Hub
* Creates container
* Starts container

---

## 2. Why does systemctl not work inside a container?

Containers:

* Do not run full init system (systemd)
* Do not control the host kernel
* Should run a single foreground process

---

## 3. What happens if the CMD process stops?

The container stops immediately.

---

## 4. Can we have multiple CMD instructions?

Yes, but only the last CMD is executed.

---

## 5. Does EXPOSE open a port?

No. It is only documentation.
Port mapping is done using `-p`.

---

# Best Practices (Interview Important)

* Use minimal base image
* Use specific version tags (avoid latest in production)
* Combine RUN commands to reduce layers
* Use .dockerignore
* Do not run containers as root in production
* Keep containers stateless

---

# Quick Revision Summary

* Image = Blueprint
* Container = Running instance
* docker run = pull + create + start
* RUN = build time
* CMD = run time
* EXPOSE = documentation only
* -p = port mapping
* systemctl does not work inside container

---
