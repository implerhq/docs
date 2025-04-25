---
description: >-
  Get data delivered straight into your application whenever a user imports a
  file using Impler.
icon: webhook
---

# Using Webhook

Once the user completes importing the spreadsheet via the widget, **Impler** sends the imported data to the callback URL specified in the `destination` section.

If your callback URL is protected, you can enable **header-based authentication**. This ensures secure data transfer to your API endpoints.

### How to add a Webhook Destination?

To configure a webhook destination in Impler:

1. Open the **Import** panel and navigate to the **Destination** section.
2. Enable the **Webhook** option.
3. Provide the **REST API Endpoint** of your application.
4. (Optional) Provide values for authentication and retry configuration.

> 🔒 Use `authHeaderName` and `authHeaderValue` if your endpoint requires authentication.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Steps to Add Webhook Destination</p></figcaption></figure>

### Chunk Size

You can configure the number of records sent per request by specifying a `Chunk Size`. This determines how many records Impler will include in a single webhook payload.

### Authentication

To secure your API, Impler supports **header-based authentication**.

* Use the `authHeaderName` field to define the name of the header.
* Use the `authHeaderValue` prop in the `import` button to define its value.

These values are not visible to end users and are only transmitted when the webhook is triggered.

For integration help, refer to: [#providing-authentication-header-value](../importer/react-embed.md#providing-authentication-header-value "mention") for React and  [#providing-authentication-header-value](../importer/html-js-embed.md#providing-authentication-header-value "mention") for HTML & JS Embed.

### Rate Limiting & Retry Mechanism

To ensure reliable data delivery and avoid data loss during transient errors or server-side rate limits, Impler supports a configurable **retry mechanism**. This is particularly useful when your webhook endpoints are subject to rate-limiting or temporary unavailability.

#### **How Retry Works**

When a webhook request to your endpoint fails (due to timeouts, rate-limiting responses like `429 Too Many Requests`, or other non-2xx errors), `Impler` will retry the request based on the following two parameters:

* **`Retry Count`**: Defines how many times Impler will attempt to resend the data after the initial failure.
* **`Retry Interval`**: The interval (in milliseconds) between each retry attempt.

> 📝 **Note:** If not configured, Impler will not retry by default (`RetryCount = 0`).

#### **Developer Notes**

* The retries apply **per chunk** of data sent.
* Retries apply only for failed HTTP responses (non-2xx).
* If the final retry still fails, the chunk is considered **undelivered**, and a failure log is recorded.
* Ensure your API implements **idempotency** to handle retries safely without duplicate processing.
* If your server enforces rate limits (like 10 requests/second), set `RetryInterval` accordingly (e.g., 1000ms or more).
* Combine with **Authentication Headers** for secure, controlled access.

### Webhook Data Format

<table data-full-width="false"><thead><tr><th width="217.33333333333337">Name</th><th width="487">Description</th></tr></thead><tbody><tr><td>template</td><td><code>CODE</code> of the template used for import</td></tr><tr><td>uploadId</td><td>Unique identifier for the upload</td></tr><tr><td>data</td><td>Array of data in JSON format</td></tr><tr><td>totalRecords</td><td>Total number of records in uploaded spreadsheet</td></tr><tr><td>totalPages</td><td>Total number of pages the data is split into</td></tr><tr><td>page</td><td>Current page number being sent</td></tr><tr><td>pageSize</td><td>Number of records in this chunk</td></tr><tr><td>extra</td><td>Extra string or JSON if it's being passed to <code>Import</code> button</td></tr></tbody></table>

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}
