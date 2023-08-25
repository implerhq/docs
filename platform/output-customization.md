---
description: >-
  Explore how developers can tailor their webhook calls to match their specific
  needs
---

# 🤠 Output Customization

This powerful feature grants you the flexibility to receive data in a format that aligns perfectly with your requirements.

Let's delve into the structure, customization options, and benefits of this output customization facility.

## Customization Structure

The output customization format follows this structured template:

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

### Dynamic Record Formatting

Key elements enclosed with `%` symbols, such as `%data%`, are treated as placeholders for traversing records. Impler interprets these keys as templates for your data records.

As new columns are added, deleted or updated, Impler dynamically adds new keys to this record format, ensuring your output stays synchronized with your columns.

### Developer Customization

Developers have the freedom to customize keys in the schema, but the values they associate with these keys must remain wrapped in `{{}}` curly braces.

This standardization ensures that Impler accurately replaces these placeholders with actual data values during webhook calls.

### Versatility and Value

This functionality empowers developers in various sectors, like **Master Data Management (MDM)**, by streamlining their data import processes.

With this feature, MDM teams no longer need to build dedicated apps for data import. Instead, they can directly import data into their MDM platforms, saving time and effort.

### Benefits at Glance:

* **Flexibility**: Customize output format to match your exact needs.
* **Simplicity**: Utilize `%`-enclosed keys for dynamic record formatting.
* **Adaptability**: New columns seamlessly integrate into the output structure.
* **Developer Freedom**: Customize keys while adhering to value placeholders.
* **Value for MDM**: Simplify data import directly into MDM platforms.

This output customization capability empowers you to direct imported data to any destination and in any preferred format.

Impler's dedication to customization facilitates seamless integration and streamlines data workflows, making complex data imports more accessible and efficient.

