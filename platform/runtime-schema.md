---
description: >-
  An essential tool that allows developers to dynamically provide schema
  information at the time of opening an import widget
---

# 🛸 Runtime Schema

This versatile feature provides flexibility and customization to the import process, catering to various use cases and dynamic requirements. Let's understand how to effectively utilize this feature.

## Getting started

To harness the power of Runtime Schema Provisioning, you'll need to access the `showWidget` function, which is exported from the `useImpler` hook. This function allows you to specify the schema at the time of invoking the import widget.

Here is the sample code,

```javascript
import { useImpler } from '@impler/react';

const { showWidget, isImplerInitiated } = useImpler({
    templateId: "...",
    projectId: "...",
    accessToken: "...",
});

function onShowClick = () => {
    showWidget({
        colorScheme,
        schema: [
            {
                key: 'Country',
                selectValues: ['India', 'China', 'USA', 'Canada'],
            },
        ],
    })
}

<button onClick={onShowClick} disabled={isImplerInitiated}>Import</button>
```

## Overriding schema properties

When providing the schema at runtime, developers can override specific schema properties. The following keys can be overridden for an existing schema:

* `key (required)`: The column key to override in the schema, which must match the key provided while creating the schema in the web portal.
* `type (optional)`: One of the types from `String`, `Number`, `Date`, `Email`, `Regex`, `Select`, and `Any` to override the existing type for the column.
* `isRequired (optional)`: A boolean value indicating whether values in the current column are required.
* `isUnique (optional)`: A boolean value indicating whether values in the current column must be unique.
* `selectValues (optional)`: Select values indicating what are the possible values when the type is select.
* `regex (optional)`: A regular expression to override when the type is `regex`.

Any key provided in the `schema` at runtime will override the corresponding property of the default schema, ensuring the flexibility to adapt the schema as needed.

## Usecases

The Runtime Schema Provisioning feature in Impler serves various use cases, including but not limited to:

1. **Dynamic Select Values**: Providing select values at runtime based on specific client requirements.
2. **Custom Validation Rules**: Overriding column types and validation rules to accommodate unique data scenarios.

## Application of Runtime Schema

The runtime schema comes into play during several crucial phases:

* **Download Sample**: When a user clicks on the "Download Sample" button, the runtime schema is applied to generate a sample file that aligns with the specified schema properties.
* **Import Process**: During the actual import, the runtime schema is used to validate and process incoming data, ensuring that it conforms to the dynamically provided schema.

The Runtime Schema Provisioning feature in Impler empowers developers to adapt and customize import processes on the fly.

This dynamic capability enhances the versatility and adaptability of the Impler platform, accommodating various data import scenarios with ease.
