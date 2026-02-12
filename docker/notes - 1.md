

---

# DAY 1: DevOps-Focused Concepts

---

# 1. What is DevOps?

DevOps = Development + Operations

Goal:

* Faster releases
* Automation
* Stability
* Continuous delivery

Dev handles:

* Writing code

Ops handles:

* Deployment
* Servers
* Monitoring
* Production issues

DevOps connects both using automation tools.

---

# 2. Application Architecture (Important for DevOps)

## Monolithic Architecture

* Entire application in one codebase
* Single WAR/EAR file
* Runs on Tomcat, JBoss, WebLogic

### DevOps Problems:

* Large size (150–200MB)
* Slow startup
* Small change → full redeploy
* Scaling entire app (not individual component)
* Downtime during deployment

---

## Microservices Architecture

Application split into small services:

* Cart
* Catalogue
* Shipping
* Payment

Each:

* Independent
* Separate deployment
* Separate scaling

### DevOps Benefits:

* Deploy only changed service
* Faster boot time
* Independent scaling
* Smaller container images
* Better CI/CD pipelines

Modern DevOps prefers Microservices.

---

# 3. Virtualisation vs Containerisation

## Virtualisation

* Each VM has full OS
* Heavy (GBs)
* Slow boot time
* Expensive

Used in:

* Traditional data centers

---

## Containerisation

* Shares host OS kernel
* Lightweight (MBs)
* Fast startup
* Portable

Used in:

* Cloud
* Microservices
* Modern DevOps

DevOps standard = Docker + Kubernetes

---

# 4. AMI vs Docker Image

## AMI (Amazon Machine Image)

Contains:

* OS
* System packages
* Runtime
* App
* Libraries

Heavy and slow to provision.

---

## Docker Image

Contains:

* Minimal OS
* App runtime
* Code
* Dependencies

Lightweight and fast.

---

# 5. Docker Core Concepts

## Image

* Static template
* Read-only

## Container

* Running instance of image

Image → Run → Container

---

## Important Docker Commands (Must Know in DevOps)

```bash
docker ps        # Running containers
docker images    # List images
docker pull nginx
docker run nginx
docker stop <containerID>
docker rm <containerID>
docker rmi <imageID>
```

Remember:
`docker run = pull + create + start`

---

# 6. Deployment Environments

Standard pipeline:

DEV → SIT → UAT → PROD

DevOps role:

* Automate deployments
* CI/CD pipelines
* Monitor production
* Rollbacks
* Zero downtime deployment

---

# 7. Support Model (Production)

L1 → Basic monitoring
L2 → Technical troubleshooting
L3 → Developers

DevOps usually:

* Between L2 and L3
* Handles infra, deployment, and logs

---

# 8. Application Servers (Interview Favorite)

* Apache Tomcat
* JBoss / WildFly
* WebLogic
* WebSphere

Used to deploy:

* WAR files
* EAR files

---

# PART 2: Interview-Focused Explanation

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

# If You Remember Only 10 Things for Interview

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
