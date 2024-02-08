---
description: What do you need to run Impler locally and how to perform the setup?
---

# 💎 Run Impler locally

## Requirements

* Node.js version v16.15.1
* MongoDB
* RabbitMQ
* localstack (required for storing files)
* (Optional) pnpm - Needed if you want to install new packages

You can also run docker containers for MongoDB, RabbitMQ, and Localstatck.

## Setup the project

After installing the required services on your machine, you can clone and setup your forked version of the project:

* Fork [Impler's repository](https://github.com/implerhq/impler.io). Clone or download your fork to your local machine.
* Run the initial setup command `npm run setup:project` to install and build all dependencies.
* Run the project locally using `npm run start:dev`

The `npm run start:dev` will start all of the services in parallel including APIs and Widget clients. if you only want to run parts of the platform, you can use the following run commands from the root project.

* **start:api** - Starts the API in watch mode
* **start:dal** - Builds the Data Access Layer package in watch mode
* **start:embed** - Serves the embed script via HTTP, which is required to open the widget
* **start:widget** - Starts the widget project that shows the widget inside an iframe
* **start:queue-manager** - Starts the Queue manager application that process sending data via webhook
* **start:widget-demo** - Starts the demo application for the widget

## Set up your environment variables

The command `npm run setup:project` creates default environment variables that are required to run Impler in a development environment. You can change them based on your requirements. These are all the available environment variables:

<details>

<summary>API Backend</summary>

* `NODE_ENV` - The environment of the app. Possible values are: dev, prod, and local
* `PORT` - The port on which the API backend should run
* `FRONT_BASE_URL` - The base URL on which your widget is available. (e.g. widget.impler.io)
* `RABBITMQ_CONN_URL` - The URL of your RabbitMQ instance
* `MONGO_URL` - The URL of your MongoDB instance
* `S3_LOCALSTACK` - The AWS endpoint for the S3 Bucket required for storing various media
* `S3_REGION` - The AWS region of the S3 Bucket
* `S3_BUCKET_NAME` - The name of the S3 Bucket
* `ACCESS-KEY` - Optional key to secure APIs

</details>

<details>

<summary>Queue Manager</summary>

* `NODE_ENV` - The environment of the app. Possible values are: dev, prod, and local
* `RABBITMQ_CONN_URL` - The URL of your RabbitMQ instance
* `MONGO_URL` - The URL of your MongoDB instance

</details>

<details>

<summary>Widget Demo</summary>

* `VITE_PROJECT_ID` - ID of the project created from API
* `VITE_ACCESS_TOKEN` - Optional token if APIs are secured
* `VITE_TEMPLATE` - Optional Template ID or Code to select template by default

</details>

<details>

<summary>Widget</summary>

* `REACT_APP_API_URL` - The URL of API

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
* **5173** - Widget Demo
