---
description: Get data right into the application whenever the user imports the file
icon: webhook
---

# Using Webhook

Once the user completes importing the spreadsheet in the widget, the impler sends imported data to the callback URL mentioned in the **destination**.

If the callback URL is protected, there is a facility to add **header-based authentication**. To activate it you can mention `authHeaderName` in the **destination section** and its value to the `import` button as `authHeaderValue` prop.

## How to add Webhook Destination?

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption><p>Steps to add Webhook Destination</p></figcaption></figure>

1. Open the Import and go to the `Destination` section.
2. Enable `Webhook`.
3. Provide REST API  Endpoint of your application.

## Chunk Size

You can provide `Chunk Size` too, which defines how many records Impler will send you in one request.

## Authentication

Impler will call your API endpoint from the server, so it will not be visible to anyone. For additional security, you can provide `Auth Header Name` which will be the key of headers sent, while the value will be taken from the application when import starts.

Details to provide `Auth Header Value` is available at [#providing-authentication-header-value](../importer/react-embed.md#providing-authentication-header-value "mention") for react and at [#providing-authentication-header-value](../importer/html-js-embed.md#providing-authentication-header-value "mention") for HTML & JS Embed.

## Webhook Data Format

<table data-full-width="false"><thead><tr><th width="217.33333333333337">Name</th><th width="487">Description</th></tr></thead><tbody><tr><td>template</td><td><code>CODE</code> of the template</td></tr><tr><td>uploadId</td><td>Upload ID</td></tr><tr><td>data</td><td>Array of data in JSON format</td></tr><tr><td>totalRecords</td><td>Total number of records in uploaded spreadsheet</td></tr><tr><td>totalPages</td><td>Total number of pages the data is divided on</td></tr><tr><td>page</td><td>Current page number</td></tr><tr><td>pageSize</td><td>Size of the data being sent</td></tr><tr><td>extra</td><td>Extra string or JSON if it's being passed to <code>Import</code> button</td></tr></tbody></table>

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
