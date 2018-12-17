# docker-compose-nginx-proxy
Customized Docker Compose template for nginx proxy. Create virtual hosts and SSL certificates automatically for other projects.
Contains the following Docker images:

- [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)
- [jrcs/letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)


## Usage
Create an external network, so other Docker containers can make use of it:

```
docker network create nginx-proxy
```

Copy the default .env file and set the COMPOSE_PROJECT_NAME.

```
cp .env.default .env
```

Run docker-compose to start the service containers:

```
docker-compose up -d
```

When you want to use the nginx proxy with other Docker Compose projects, add the following network configuration:

```
networks:
  default:
    external:
      name: nginx-proxy
```
