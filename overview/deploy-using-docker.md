---
description: Docker compose is the easiest way to get started with self-hosted Impler
---

# 🐋 Deploy using Docker

## Before you begin

You need the following installed in your system:

* [Docker](https://docs.docker.com/engine/install/) and [docker-compose](https://docs.docker.com/compose/install/)
* [Git](https://git-scm.com/downloads)

## Quick start

Clone the repository, get into the docker directory, and start the containers.

```
# Get the code
git clone --depth 1 https://github.com/implerhq/impler.io

# Go to the docker folder
cd impler.io/docker

# Copy the example env file
cp .env.example .env

# Update the following AWS S3 credentials in the .env file
S3_LOCAL_STACK=http://localhost:4566
S3_BUCKET_NAME=impler
S3_REGION=us-east-1
AWS_ACCESS_KEY_ID=test
AWS_SECRET_ACCESS_KEY=test

# Start Impler
docker-compose up
```

After the application containers are started, you can visit [http://localhost:4200](http://localhost:4200) to start playing with Impler.

## Configuration

To help you get started fast, we have integrated the following services with docker-compose,

* `rabbitmq` - Used to communicate between `api` and `queue-manager`
* `mongodb` - Used as a database

We recommend you decouple the database in order to keep the data safe.

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
