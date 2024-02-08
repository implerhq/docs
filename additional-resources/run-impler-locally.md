---
description: What do you need to run Impler locally and how to perform the setup?
---

# 💎 Run Impler locally

## Requirements

* Node.js version v18.13.0
* MongoDB
* RabbitMQ
* localstack (required for storing files)
* (Optional) pnpm - Needed if you want to install new packages

You can also run docker containers for MongoDB, RabbitMQ, and Localstatck.

## Setup the project

After installing the required services on your machine, you can clone and set your forked version of the project:

* Fork [Impler's repository](https://github.com/implerhq/impler.io). Clone or download your fork to your local machine.
* Run the initial setup command `npm run setup:project` to install and build all dependencies.
* Run the project locally using `npm run start:dev`

The `npm run start:dev` will start all of the services in parallel including APIs and Widget clients. if you only want to run parts of the platform, you can use the following run commands from the root project.

* **start:api** - Starts the API in watch mode
* **start:dal** - Builds the Data Access Layer package in watch mode
* **start:embed** - Serves the embed script via HTTP, which is required to open the widget
* **start:widget** - Starts the widget project that shows the widget inside an iframe
* **start:queue-manager** - Starts the Queue manager application that processes sending data via webhook
* **start:web** - Starts the web application, where you can create manage imports.

You can run `pnpm start:<APP>` command one by one too, in case you want to run applications separately.

## Set up your environment variables

The command `npm run setup:project` creates default environment variables that are required to run Impler in a development environment. You can change them based on your requirements. These are all the available environment variables:

<details>

<summary>API Backend</summary>

* `JWT_SECRET` - The secret token used to create jsonwebtoken.
* `NODE_ENV` - The environment of the app. Allowed values are: _dev_, _prod_, and _local_
* `PORT` - The port on which the API backend should run
* `FRONT_BASE_URL` - The base URL on which your widget is available. (e.g. widget.impler.io)
* `RABBITMQ_CONN_URL` - The URL of your RabbitMQ instance
* `MONGO_URL` - The URL of your MongoDB instance



* `S3_LOCALSTACK` - The AWS endpoint for the S3 Bucket required for storing various media
* `S3_REGION` - The AWS region of the S3 Bucket
* `S3_BUCKET_NAME` - The name of the S3 Bucket
* `AWS_ACCESS_KEY` - A unique identifier granting access to AWS services
* `AWS_SECRET_ACCESS_KEY` - A confidential key used for secure authentication to AWS services

<!---->

* `WIDGET_BASE_URL` - Base URL of widget without any path. Example, http://localhost:3500
* `WEB_BASE_URL` - Base URL of the web without any path. Example, http://localhost:4200

<!---->

* `COOKIE_DOMAIN` - Base domain used to set cookies
* `GITHUB_OAUTH_REDIRECT` - URL where GitHub OAuth redirects after authentication
* `GITHUB_OAUTH_CLIENT_ID` - Unique identifier for client application when using GitHub OAuth
* `GITHUB_OAUTH_CLIENT_SECRET` - Confidential key for client application authentication in GitHub OAuth

<!---->

* `SES_REGION` - Region identifier for Amazon SES (Simple Email Service) configuration
* `SES_ACCESS_KEY_ID` - Unique identifier granting access to Amazon SES (Simple Email Service)
* `SES_SECRET_ACCESS_KEY` - Confidential key used for secure authentication to Amazon SES (Simple Email Service)
* `EMAIL_FROM` - Email address used as the sender when sending emails
* `EMAIL_FROM_NAME` - Name associated with the sender's email address when sending email

</details>

<details>

<summary>Queue Manager</summary>

* `NODE_ENV` - The environment of the app. Possible values are: dev, prod, and local
* `RABBITMQ_CONN_URL` - The URL of your RabbitMQ instance
* `MONGO_URL` - The URL of your MongoDB instance

<!---->

* `S3_LOCALSTACK` - The AWS endpoint for the S3 Bucket required for storing various media
* `S3_REGION` - The AWS region of the S3 Bucket
* `S3_BUCKET_NAME` - The name of the S3 Bucket
* `AWS_ACCESS_KEY` - A unique identifier granting access to AWS services
* `AWS_SECRET_ACCESS_KEY` - A confidential key used for secure authentication to AWS services

</details>

<details>

<summary>Widget</summary>

* `REACT_APP_API_URL` - The base URL of the API. Example, http://localhost:3000
* `REACT_APP_ENVIRONMENT` - The environment of the app. Allowed values are: _dev_, _prod_, and _local_

</details>

<details>

<summary>Web</summary>

* `NEXT_PUBLIC_API_BASE_URL` - The base URL of API. Example, http://localhost:3000
* `NEXT_PUBLIC_EMBED_URL` - Full url of embed script. Example, http://localhost:4701/embed.umd.min.js

</details>

## Running Tests

Writing tests are currently In Progress. You can test packages or apps using appropriate CLI commands:

### API

To run the API tests, run the following command:

```
npm run test:api
```

## Ports used by services when the project spins up

* **3000** - API
* **4701** - Embed
* **3500** - Widget
* **4200** - Web

## [Running Migrations](run-impler-locally.md#running-migrations)

We're always around in [Discord](https://discord.impler.io). Please join if you didn't, would love to answer your questions, and solve your queries.
