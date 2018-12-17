# docker-compose-nginx-proxy
Docker Compose template for nginx proxy. Create virtual hosts and SSL certificates automatically for other projects.
Contains the following Docker images:

- [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)
- [jrcs/letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)


## Usage
Create an external network, so other Docker containers can make use of it:

```
docker network create nginx-proxy
```

**Optional**: If you want to change the Docker Compose project name, copy the default .env file and set the COMPOSE_PROJECT_NAME.

```
cp .env.default .env
```

**Optional**: If you want to add some custom configuration, add a Docker Compose override file.

For example, if you want to add a custom nginx configuration file:
- Create an override file:

  ```
  touch docker-compose.override.yml custom.conf
  ```

- Add the following to this the file:

  ```
  version: "3"

    services:
      proxy:
        volumes:
          - ./custom.conf:/etc/nginx/conf.d/custom.conf
      ssl:
        volumes:
          - ./custom.conf:/etc/nginx/conf.d/custom.conf
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
