---
description: >-
  The Multiselect feature in Impler allows users to pick multiple values for a
  single cell. This feature is useful in various scenarios like selecting
  categories for products, tagging items, and more.
icon: list-dropdown
---

# Multiselect Dropdown

### i. Enable Multiselect from web portal

1. Click on the `+` button to add a new column.
2. Provide column `Name` and `Type` = `Select`.

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>Add Select Column</p></figcaption></figure>

3. Click on `Validations`.

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Multiselect Validations</p></figcaption></figure>

4. We can provide allowed values in `Select Values`.
5. We can also enable Multi Select for select column. Which allows user to select multiple values in the cell.

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>Specifying Delimiter</p></figcaption></figure>

6. Additionally we can sepcify `,` or `;` as delimiter for multi-select values.

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
      allowMultiSelect: true,
      delimiter: ';'
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

Columns with the Multiselect feature will send an array of selected values when sent to application [using-webhook.md](../data-retrieval/using-webhook.md "mention") or [using-frontend-callback.md](../data-retrieval/using-frontend-callback.md "mention").

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}
