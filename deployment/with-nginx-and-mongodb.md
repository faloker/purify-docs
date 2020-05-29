# With Nginx and MongoDB

## Overview

This deployment is based on two docker images:

1. [https://hub.docker.com/r/faloker/purify-api](https://hub.docker.com/r/faloker/purify-api)
2. [https://hub.docker.com/r/faloker/purify-nginx](https://hub.docker.com/r/faloker/purify-nginx)
   1. serve static files \(vue frontend\)
   2. provide https
   3. serve files over http2
3. [https://hub.docker.com/\_/mongo](https://hub.docker.com/_/mongo) \(if you want local mongodb\)

## Local setup

To start the Purify locally without certificates and other production things, you can do the following:

1. Clone repository
2. Run `docker-compose -f docker-compose.tests.yml up --build`

## Configuration

### docker-compose

Before deployment you may want to configure a few things in docker-compose file

```text
// ./docker-compose.yml

// if you want local mongodb
mongo:
...
environment:
  MONGO_INITDB_ROOT_USERNAME: root
  MONGO_INITDB_ROOT_PASSWORD: example


// update local path to the .env file (see api/.env.example)
api:
...
env_file:
  - .env.custom


// update local paths to certificate and key files
nginx:
...
volumes:
      - /path/to/cert:/etc/nginx/ssl/cert
      - /path/to/key:/etc/nginx/ssl/key
      - ./nginx.prod.conf:/etc/nginx/nginx.conf
```

### nginx

You can edit nginx config file to adjust it for your needs. There is a config [example](https://github.com/faloker/purify/blob/master/nginx/nginx.prod.conf) which is used by default, but in order to use it, you will need to change [server\_name](https://github.com/faloker/purify/blob/master/nginx/nginx.prod.conf#L25) options.

## Start

```text
docker-compose up -d
```

