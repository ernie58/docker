## Wat is docker?

Docker is the world's leading software containerization platform  
  
On the website:  
Docker containers wrap a piece of software in a complete filesystem that contains 
everything needed to run: code, runtime, system tools, system libraries – 
anything that can be installed on a server. This guarantees that the software will always run the same, regardless of its environment

#VSLIDE

## Before we start

Vorige week heeft Docker zijn website geüpdate.
Niet enkel zijn website, maar ook zijn software. last-minute rewrite

#VSLIDE

## TOC

- Docker platform
- Containers
- Docker compose
- Swarm (beperkt)
- ...

HSLIDE

## Docker platform: for developers
- Build test, deploy and debug any language or stack without incompatibility or version conflict:
- 65% less setup work to join a project installing servers and software
- mimic production with built-in orchestration

#VSLIDE

## Docker platform: for ops
- ship software 13x more frequently
- Quickly scale (orchestration)
- Efficiency: easier deploy, reduce it cost, reduce downtime, quickly roll back
- distribute images in docker registries, automatically synchronize updates
- apps work everywhere
- out of the box security (Docker content trust)

#VSLIDE

## Docker platform: for the enterprise
- one platform for everything
- automate deployment pipelines (CI/CD)
- Docker is extendible with API's and plugins
- CI/CD
- infrastructure optimization (load, performance, cost)
- apps are portible to every cloud infrastructure

#VSLIDE

## Docker platform: 2 editions
- Community edition
- Enterprise edition

#VSLIDE

## Docker platform: Community edition
- bevat docker engine
- ideaal voor developers en kleine teams
- installs voor mac, windows, aws, azure, + aantal linux distros
- Unlimited public and one free private repo aas
- automated builds

#VSLIDE

## Docker platform: Community edition
- Downloads available for Windows & Mac
- easy to install desktop apps die integreren met virtualisatie van host os
- Docker word volledig geintegreerd met de bestaande omgeving
- Enkel Windows 10:
  - vereist Hyper-V, waardoor Virtualbox niet meer werkt
  - Oplossing: Docker-machine gebruiken 

#VSLIDE

## Docker platform: Enterprise edition
- docker engine on certified infrastructure
- installs windows server, aws, azure, + aantal linux distros
- certified container, plugins, ...
- Docker datacenter
- web interface/role based access/LDAP
- extended support
- 750$ per node per year

#VSLIDE

## Docker platform: andere componenten
- Docker cloud: hosted service for building, testing and deploying images
- Docker Universal Control Plane: enterprise-grade cluster management solution
- Docker compose (define applications with multiple containers)
- Docker Trusted Registry (store and sign docker images)
- Docker machine: automate container provisioning

#HSLIDE

## What are containers

(what is a container)[https://www.docker.com/sites/default/files/what_is_a_container.png]

## containers vs virtual machines

(Container) [https://www.docker.com/sites/default/files/Container%402x.png]

## containers vs virtual machines

(VM) [https://www.docker.com/sites/default/files/VM%402x.png]

#VSLIDE

## Containers and VMs together are great

(together) [https://www.docker.com/sites/default/files/containers-vms-together.png]

#VSLIDE

## Containers

- Containers include the application and all of its dependencies   
- They share the kernel with other containers, running as isolated processes in user space on the host operating system.   
- Docker containers are not tied to any specific infrastructure: they run on any computer, on any infrastructure, and in any cloud.  

#VSLIDE

## Containers
troeven:  
  - lightweight
    - layered containers
    - shared kernel
  - open standard
    - runs on every infrastructure
  - secure
    - isolate applications from infrastructure and each other

## Docker compose
- tool for defining and running multi-container Docker applications
- file: docker-compose.yml
- CLI: build and  run environment

## A docker-compose.yml looks like this:
```
version: '2'
services:
  web:
    build: .
    ports:
    - "5000:5000"
    volumes:
    - .:/code
    - logvolume01:/var/log
    links:
    - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
  ```

## with the CLI you can:
- Start, stop and rebuild services
- View the status of running services
- Stream the log output of running services
- Run a one-off command on a service
- ...

## Use cases
- Development environments
- Automated testing environments
- Traditionally developed for single host deployments
  - lately more and more production-oriented features
  - you can deploy to single instance engine or complete swarm

## Demo

## Steps
- Create a directory for the project
- Create an app
- Create a Dockerfiles
- Create compose file
- Build and run

## Compose CLI reference

## Compose file reference
- currently version 3 (recommended, compatible with docker swarm)
- define services, networks and volumes
- see official documentation
- you can combine multiple compose file to extend each other (eg. for production)

## het verschil tussen Docker machine en Docker for Mac, Windows,...

De docker toolbox (machine, engine and compose)

Docker machine spins VMs on virtualbox that contain docker engine and the boot2docker linux distro
Docker for Mac is a native app, with symlinks for docker and docker-compose. It doesn't use Virtualbox, but Hyperkit (lightweight virtualisation) It sets up one VM for you, on wich it runs containers
Docker for windows is the same as docker toolbox, but it uses Hyper-V, which conflicts with Virtualbox. It enables you to run containers on Windows directly.
