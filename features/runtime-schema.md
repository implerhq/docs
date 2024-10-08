---
description: >-
  Do you need to import data in columns that are not fixed firsthand? Impler
  provides a facility to provide schema at the moment of opening the import
  widget.
icon: eye-slash
---

# Runtime Schema

{% hint style="info" %}
Available after the impler version `0.9.1`&#x20;
{% endhint %}

## Purpose

Consider you have an ERP application that needs to import sales information. Our system provides a way to add extra information to sales information, like `challan-no`. Other users might have different columns.

In that case, fixing the import data structure is impossible. So we need to pass schema during run time when the user clicks on `Import` button to import the data.

You can find relevant implementation for react in [#providing-runtime-schema](../importer/react-embed.md#providing-runtime-schema "mention")and for HTML & HS in [#providing-runtime-schema](../importer/html-js-embed.md#providing-runtime-schema "mention")

## Example Schema

```
[
  {
    name: 'Name',
    key: 'name',
    type: 'String'
  },
  {
    name: 'Phone',
    key: 'phone',
    type: 'Number',
    defaultValue: '#########'
  },
  {
    name: 'Country',
    key: 'country',
    type: 'String'
  }
]
```

## Available properties for schema

Here are the keys&#x20;

* `name (required)`: The name of the column, will be displayed in the import widget during mapping.
* `key (required)`: The key of the column, will be used to create an Excel file and match it with available headings in the file.
* `type (optional)`: One of the types from `String`, `Number`, `Date`, `Email`, `Regex`, `Select`, and `Any` to override the existing type for the column.
* `isRequired (optional)`: A boolean value indicating whether values in the current column are required.
* `isUnique (optional)`: A boolean value indicating whether values in the current column must be unique.
* `selectValues (optional)`: Select values indicating what are the possible values when the type is select.
* `regex (optional)`: A regular expression to override when the type is `regex`.
* `dateFormats (optional)`: Date formats indicating a list of formats acceptable for the date field. Required when type is `Date`. For example, `['dd/mm/yyyy','dd/mm/yy']`

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
