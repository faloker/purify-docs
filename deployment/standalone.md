# Standalone

## Overview

This deployment is based on a single image:

1. [https://hub.docker.com/r/faloker/purify](https://hub.docker.com/r/faloker/purify)
   1. static files served by the web server

In this deployment scenario, you need to provide load balancing and database layers on your own.   
Good example is to use it with something like Heroku and MongoDB Atlas.

## Configuration

Create your own **.env** file based on this [example](https://github.com/faloker/purify/blob/master/api/.env.example): 

```text
# any random quite long string
JWT_SECRET=changeme

# pass uri with credentials if needed
MONGODB_URI=mongodb://root:example@mongo:27017

# just any string
DB_NAME=purify

# domain where purify is running, e.g. purify-demo.herokuapp.com
DOMAIN=purify-demo.herokuapp.com
```

## Start

```text
docker run --env-file=.env.custom -p 8000:3000 faloker/purify
```

Also, you can provide an environment variable **PORT** to start Purify instance on a specific port.

