---
icon: sidebar
description: >-
  Freeze columns in excel and editor to better view data while editing and
  adding records
---

# Freeze Columns

## Three ways to freeze columns

We can freeze columns in many ways. Here is how,

### i. Freeze the column while adding a new one

1. Click on the `+` button to add a new column.
2. Provide column `Name`, `Key name` and rest of the values based on your choice.
3. Check `Frozen?` checkbox for the column.

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption><p>Freezing column while adding new one</p></figcaption></figure>

### ii. **Freezing already created column**

1. Click on the Pencil (Edit) icon for any created column.
2. Check the `Frozen?` checkbox.
3. Click on `Save`.

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption><p>Editing the column to mark it as freeze</p></figcaption></figure>

### iii. Freezing column with [Runtime Schema](runtime-schema.md)

We can freeze the column while providing a custom schema too with the `isFrozen` flag in our frontend code.

```javascript
showWidget({
  schema: [
    {
      key: 'email',
      name: 'Email',
      type: 'Email',
      isFrozen: true
    }
  ]
});
```

## Effects on Sample File Generation

The generated sample file will have specified columns freeze on the left side. So they won't gets hidden if we scroll to the right.

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption><p>Excel view of freezed columns</p></figcaption></figure>

## Effects on Spreadsheet Editor

While importing data spreadsheet editor freezes two default `Checkbox` and `Sr. No.` Columns. Other mentioned columns get frozen as per schema.

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption><p>Freezing 2 default and 2 mentioned columns in editor</p></figcaption></figure>

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}
