---
icon: message-exclamation
---

# Column Warning

The Warning Column feature allows you to show helpful suggestions to users without blocking their data import. Unlike errors that stop the import process, warnings let users proceed while highlighting potential issues.

## How it Works

#### Two Types of Validations

| Validation Type | Behaviour                     | Visual Indicator  |
| --------------- | ----------------------------- | ----------------- |
| Errors          | Block data submission         | Red background    |
| Warning         | Allow submission with notices | Yellow background |

#### Key Benefits

* **Key Benefit**: Users are informed of any issues through warnings, but their uploads aren’t blocked.

## Implementation Guide

#### Basic Structure

Every warning validation function follows this pattern:

```
const axios = require('axios');
exports.code = async (params) => {
  const result = [];
  // Loop through each item in the dataset
  for (const item of params.data) {
    result.push({
      index: item.index,
      warnings: {
        Country: 'Please specify your country',
      },
    });
  }

  return result;
};;

```

<figure><img src=".gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

{% include ".gitbook/includes/your-feedback-is-crucial-in....md" %}
