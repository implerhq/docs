---
description: Guide on how to define schema for your import needs
---

# 🧰 Configure Import

Impler is organized in the structure of `Project`, `Template` and `Columns`.&#x20;

The **project** is an entry point for your import needs. The project organizes your import that belongs to the same development goal.

The **template** represents individual imports. For example, you would like to import employee data into your HRM system.

The **column** represents individual fields in the **template**. An employee can have the `first name`, `last name`, `email`, and `address` as columns.

Here are the steps to `create a project`, `add a template to it`, and `add columns to the template`.

{% swagger method="post" path="/v1/project" baseUrl="https://api.impler.io" summary="Create a project " %}
{% swagger-description %}
Create a project that acts as a container for your imports.
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="true" %}
Name of the project
{% endswagger-parameter %}

{% swagger-parameter in="body" name="code" required="true" %}
Unique code for the project
{% endswagger-parameter %}

{% swagger-parameter in="body" name="authHeaderName" %}
Name of header key to authenticate the callback
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Created project" %}
```json
{
  "_id": "string",
  "name": "string",
  "code": "string",
  "authHeaderName": "string"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v1/template" baseUrl="https://api.impler.io" summary="Add new template for your import" %}
{% swagger-description %}
Adds a new template to the project.
{% endswagger-description %}

{% swagger-parameter in="path" name="projectId" required="true" %}
Id of the project
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" %}
Name of the import
{% endswagger-parameter %}

{% swagger-parameter in="body" name="code" required="true" %}
Unique code for the import
{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackUrl" required="true" type="URL" %}
Webhook URL that gets used to send imported data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="chunkSize" type="Number" required="true" %}
Amount of data to send via webhook
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Created template" %}
```json
{
  "_id": "string",
  "name": "string",
  "code": "string",
  "callbackUrl": "string",
  "chunkSize": 0,
  "sampleFileUrl": "string",
  "_projectId": "string"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/v1/column" baseUrl="https://api.impler.io" summary="Update columns for template" %}
{% swagger-description %}
Replaces the current columns schema with the new one. Use it to update or add schema for the template.

In the body, it accepts an array of column schema.
{% endswagger-description %}

{% swagger-parameter in="path" name="templateId" required="true" %}
Id of the template
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Array of new columns" %}
```json
[
  {
    "name": "string",
    "key": "string",
    "alternateKeys": [
      "string"
    ],
    "isRequired": false,
    "isUnique": false,
    "type": "String",
    "regex": "string",
    "regexDescription": "string",
    "selectValues": [
      "string"
    ],
    "sequence": 0
  }
]
```
{% endswagger-response %}
{% endswagger %}

### Column Schema

Column schema is how individual fields in your import look. Its includes the following fields,

<table><thead><tr><th>Field Name</th><th data-type="select">Type</th><th>Is Required?</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td></td><td>Yes</td><td>Name of the column</td></tr><tr><td>key</td><td></td><td>Yes</td><td>Heading of the field you're expecting in the spreadsheet that gets imported</td></tr><tr><td>alternateKeys</td><td></td><td></td><td>Other possible headings of the field in the spreadsheet</td></tr><tr><td>isRequired</td><td></td><td></td><td>Validation to check if the field and it's value required</td></tr><tr><td>isUnique</td><td></td><td></td><td>Validation to check if the field value should be unique</td></tr><tr><td>type</td><td></td><td>Yes</td><td>Type of the field, available types are <code>String</code>, <code>Number</code>, <code>Date</code>, <code>Email</code>, <code>Regex</code>, <code>Select</code>, and  <code>Any</code>. <code>Email</code> validates the values</td></tr><tr><td>regex</td><td></td><td>Yes if type is <code>Regex</code></td><td>Regular expressions to check against value</td></tr><tr><td>regexDescription</td><td></td><td></td><td>Description of the regular expression</td></tr><tr><td>selectValues</td><td></td><td>Yes if type is <code>Select</code></td><td>List of values that are valid</td></tr><tr><td>sequence</td><td></td><td></td><td>Sequence number to maintain the field ordering</td></tr><tr><td>apiResponseKey</td><td></td><td></td><td>The key that you want to receive  while retrieving data, default is <code>key</code></td></tr></tbody></table>

After adding columns to the template you're ready to import data into your project. You can refer to widget [getting-started.md](../widget/getting-started.md "mention") guide to add an import widget to your application.
