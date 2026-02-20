---
{"dg-publish":true,"permalink":"/docker-composer/","tags":["docker"]}
---

# Docker compose

## What is?

The `docker-compose.yml` is the file in charge to save us time in configuring each container and each time we have to set up each one.

## What is `.yml`?

It is the language that configures the docker-compose files

## Building our docker compose file

```yml
version: "3.9"

services:
  # First here we will define the name of our containers
  # And it is very important that here we has a line break
  myapp:
    # Here we specify the route of our Dockerfile
    build: .
    # Here, between "", we set the port mapping
    ports:
      - "3000:3000"
    # Here the connections with other containers based on their NAMES without ""
    links:
      - mongon

  # Here we set the db image configuration
  mongon:
    # From waht image will be created
    image: mongo
    # Ports mapping for db
    ports:
      - "27017:27017"
    # Environment variables (.env)
    environment:
      - MONGO_INITDB_ROOT_USERNAME=alan
      - MONGO_INITDB_ROOT_PASSWORD=password
```

Finally, to setup automatically all containers, we just have to execute `docker compose up` in the root path of our project. This command will create some images and containers that can be removed gracefully using the opposite command: `docker compose down`

Another good feature of using docker compose files, is that all containers declared there will be set in a network automatically

>[!QUOTE] **References**
>[https://www.youtube.com/watch?v=4Dko5W96WHg](https://www.youtube.com/watch?v=4Dko5W96WHg)

