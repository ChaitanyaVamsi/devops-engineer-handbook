
---

# PART 1: Interview-Focused Explanation

---

## What is the difference between Virtualisation and Containerisation?

Virtualisation runs multiple VMs with full OS on a hypervisor, which is heavy and slow.
Containerisation shares the host OS kernel, is lightweight, faster to start, and more portable.

Containers use fewer resources compared to VMs.

---

## What is Docker?

Docker is a containerisation platform used to package an application with its dependencies into a container, ensuring consistent environments across development, testing, and production.

---

## What is Docker Image?

A Docker image is a read-only template that contains application code, runtime, libraries, and dependencies.

---

## What is Docker Container?

A container is a running instance of a Docker image.

---

## Difference between Image and Container?

Image → Static template
Container → Running instance of image

---

## What is Monolithic Architecture?

Monolithic architecture is an application where frontend, backend, and business logic are tightly coupled and deployed as a single unit.

---

## Problems with Monolithic?

* Hard to scale
* Slow deployments
* Full application redeployment required
* Large size
* Downtime risk

---

## What are Microservices?

Microservices architecture splits an application into small independent services that communicate via APIs.

---

## Why are Microservices better for DevOps?

* Independent deployments
* Easy scaling
* Faster CI/CD
* Fault isolation
* Smaller builds

---

## What is WAR file?

WAR (Web Archive) file contains a web application including servlets, JSP, and dependencies.

---

## What is EAR file?

EAR (Enterprise Archive) contains multiple modules (WAR + JAR) used in enterprise applications.

---

## What is CI/CD?

CI – Continuous Integration
CD – Continuous Delivery / Deployment

It automates:

* Build
* Test
* Deploy

---

# Part 1 - RECAP

1. DevOps = Automation + Collaboration
2. Containers are lightweight
3. Image is not equal to Container
4. docker run = pull + create + start
5. Microservices are better than Monolithic for scalability
6. Containers boot faster than VMs
7. AMI is heavy, Docker image is lightweight
8. DEV → SIT → UAT → PROD
9. L1, L2, L3 support model
10. Docker is used for portability

---

# PART 2: Frequently Asked Interview Questions

---

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