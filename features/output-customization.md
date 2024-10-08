---
description: Customize output format to receive data in a manner that the system can use.
icon: tree-christmas
---

# Output Customization

There are chances that the system which is receiving data is not made or managed by us. But as a plugin or integration, we need to send imported data to that system. In that case, Impler allows changing the output format which follows the system's syntax.

## Output Format Sample

```json
{
  "%data%": {
    "month": "{{month}}",
    "day": "{{day}}",
    "AverageTemperatureFahr": "{{AverageTemperatureFahr}}",
    "AverageTemperatureUncertaintyFahr": "{{AverageTemperatureUncertaintyFahr}}",
    "city": "{{city}}",
    "country_id": "{{country_id}}",
    "Country": "{{Country}}",
    "Latitude": "{{Latitude}}",
    "Longitude": "{{Longitude}}"
  },
  "page": "{{page}}",
  "chunkSize": "{{chunkSize}}",
  "isInvalidRecords": "{{isInvalidRecords}}",
  "template": "{{template}}",
  "uploadId": "{{uploadId}}",
  "fileName": "{{fileName}}",
  "extra": "{{extra}}"
}
```

## Usage Examples

### Joining First Name and Last Name

```json
{
  "%data%": {
    "FullName": "{{firstName}} {{lastName}}"
  },
  "page": "{{page}}",
  "chunkSize": "{{chunkSize}}",
  "isInvalidRecords": "{{isInvalidRecords}}",
  "template": "{{template}}",
  "uploadId": "{{uploadId}}",
  "fileName": "{{fileName}}",
  "extra": "{{extra}}"
}
```

### Providing an Object for each value

```
{
  "%data%": {
    "city": {
      "label": "City",
      "id": "city",
      "value": "{{city}}"
    }
  }
}
```

### Passing an Array for value

```
{
  "%data%": {
    "address": ["{{addressLine1}}","{{addressLine2}}", "{{state}}", "{{city}}", "{{pincode}}"]
  }
}
```

## Output Format works differently for dynamic schema

If you're providing schema runtime from the application, in that case, default provided output isn't taken into consideration. Because columns defined in the output might not match with columns getting imported.

In that case, we need to provide schema runtime. We have listed examples for react in [#providing-runtime-schema](../importer/react-embed.md#providing-runtime-schema "mention") and for HTML & JS versions in [#providing-runtime-schema](../importer/html-js-embed.md#providing-runtime-schema "mention").

This output customization capability empowers you to direct imported data to any destination and in any preferred format.

Have any questions? Feel free to ping us over [discord](https://discord.impler.io).
