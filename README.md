# Docker Development Image For PHP8 and Node 16

This Dockerfile allows you to build an image for PHP8 and Node 16. This image can support development with databases such as MongoDB and MySQL, the php extensions for these DBs have been integrated. The image created will have the following packages for development

1. PHP 8.x
2. Node 16.x
3. Composer
4. PHP extensions for Mongo
5. PHP extensions for MySQL

## Exposed Ports

1. 9000
2. 5000 - 6000 (For Node)

## How to build

> **Note**: This assumes you have [Docker](https://www.docker.com/) installed in your machine.

In order to build the image follow the steps below

1. Clone the repo

```git clone https://github.com/stescacom/dev-php8-node16-img.git```

2. cd into the cloned repo
3. Run `docker build . -t <<your image tag>>`

## Use

To create a container from the built image run 
```docker run -v <<php project folder>>:/var/www << image tag >> --name << container name >>```

### Use with docker-compose.yml

In order to use the recently built image with `docker-compose.yml`, consider the following example.

```
 docker-service-name:
    image: << your image tag >>
    container_name: << container name >>
    restart: unless-stopped
    tty: true
    user: root
    environment:
      SERVICE_NAME: << service name >>
      SERVICE_TAGS: << service tag >>
    working_dir: /var/www
    volumes:
       - ".:/var/www"

```

