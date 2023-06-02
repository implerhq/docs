---
description: Get the imported spreadsheet data using REST API, whenever you want!
---

# 🥂 Using REST API

It's possible to get imported data via rest api. It is a convenient option when instead of `Impler` pushing data to your app, you want to pull the data.

To get the data (`valid`/`invalid`), you need `uploadId` that you can get when the user starts, terminate or complete the import, which you can refer at [react-embed.md](../widget/react-embed.md "mention")

Following are the URLs to receive imported data,

{% swagger method="get" path="/v1/upload/{uploadId}/rows/valid" baseUrl="https://api.impler.io" summary="Get valid uploaded data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="uploadId" type="String" required="true" %}
Upload Id to get data for
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Number" %}
Expected size of data
{% endswagger-parameter %}

{% swagger-parameter in="query" name="page" type="Number" %}
Page number of records
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Paginated data" %}
```json
{
  "page": 0,
  "data": [
    {}
  ],
  "limit": 0,
  "totalPages": 0,
  "totalRecords": 0
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v1/upload/{uploadId}/rows/invalid" baseUrl="https://api.impler.io" summary="Get invalid uploaded data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="uploadId" type="String" required="true" %}
Upload Id to get data for
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Number" required="false" %}
Expected size of data
{% endswagger-parameter %}

{% swagger-parameter in="query" name="page" type="Number" %}
Page number of records
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Paginated data" %}
```json
{
  "page": 0,
  "data": [
    {}
  ],
  "limit": 0,
  "totalPages": 0,
  "totalRecords": 0
}
```
{% endswagger-response %}
{% endswagger %}

Further, you can fetch the list of uploads using the following API,

{% swagger method="get" path="/v1/upload/{template}" baseUrl="https://api.impler.io" summary="Get list of uploads for imported files for template" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="template" type="String" required="true" %}
Id of the template
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of uploads for imported files" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
