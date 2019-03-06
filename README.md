Customized Docker Compose template for nginx proxy. Create virtual hosts and SSL certificates automatically for your Docker projects.

Contains the following Docker images:

- [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)
- [jrcs/letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)


# Getting started
Create an external network in Docker:

```
docker network create nginx-proxy
```

Copy the default .env file and configure environment variables.

```
cp .env.default .env
```

Run docker-compose to start containers:

```
docker-compose up -d
```

To run nginx-proxy with Letsencrypt:

```
docker-compose up -f docker-compose.yml -f docker-compose.prod.yml -d
```

When you want to use the nginx proxy inside other Docker Compose projects, add the following network configuration to your `docker-compose.yml`-file:

```
networks:
  default:
    external:
      name: nginx-proxy
```
