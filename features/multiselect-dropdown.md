---
description: >-
  The Multiselect feature in Impler allows users to pick multiple values for a
  single cell. This feature is useful in various scenarios like selecting
  categories for products, tagging items, and more.
---

# ✨ Multiselect Dropdown

## Enabling Multiselect Dropdown

To enable the multiselect dropdown in the Impler web portal, follow these steps:

### i. Enable Multiselect for a new column

1. Click on the `+` button to add a new column.
2. Provide column `Name`, `Key name` , and `Type` as `List` and pick `Select Values` based on your choice.
3. Check `Multi Select?` checkbox for the column.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption><p>Add Multiselect Column </p></figcaption></figure>

### ii. **Enable Multiselect for the old column**

1. Click on the Pencil (Edit) icon for any created column.
2. Mark the `Column Type` as `Select` and add appropriate values in `Select Values` field.
3. Check the `Multi Select?` checkbox.
4. Click on `Save`.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>Editing the column to enable multi select</p></figcaption></figure>

### iii. Enabling Multiselect Dropdown using [Runtime Schema](runtime-schema.md)

We can enable the Multiselect feature by providing a custom schema with the `allowMultiSelect` flag in our frontend code.

```javascript
showWidget({
  schema: [
    {
      key: 'choice',
      name: 'Eating Choice',
      type: 'Select',
      selectValues: ['Fruit', 'Vegetables', 'Nuts'],
      allowMultiSelect: true
    }
  ]
});

```

## Sample file generation and format

Impler creates `.xlsx` and `.xlsm` files based on the columns' configuration:

* **.xlsx File**: Generated if no columns have Multiselect enabled.
* **.xlsm File**: Generated if any column has Multiselect enabled.

### Writing in .xlsm Files

When a column is marked as Multiselect, Impler appends `#MULTI` to the end of the column name in the Excel file. This allows users to select multiple options in the cell.

For detailed steps on how to write in `.xlsm` files refer to [writing-effectively-into-.xlsm-files.md](../additional-resources/writing-effectively-into-.xlsm-files.md "mention").

## Data Format

Columns with the Multiselect feature will send an array of selected values when sent to the user via webhook.

## Summary

The Multiselect feature is a powerful tool that enhances the flexibility of data selection in Impler. By either using the web portal or custom schema, users can easily enable this feature to accommodate various use cases. The distinction between `.xlsx` and `.xlsm` files ensures that the data is correctly processed and displayed according to the column configurations.

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
