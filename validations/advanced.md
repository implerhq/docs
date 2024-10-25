---
icon: superpowers
description: >-
  Validations help you to ensure that data is in the format you want them to be
  in. A tooltip will be shown for invalid data and you can ensure that errors
  get resolved before data gets submitted.
---

# Advanced Validations

## Validations

#### Range

Validates that field's values for `Number` and `Double` columns fall within a `min` and `max` values. Either `min`, `max` or `both` must be defined. Values are inclusive.

<table><thead><tr><th>Name</th><th>Value</th><th data-type="checkbox">Is Required</th></tr></thead><tbody><tr><td><code>validate</code></td><td><code>range</code></td><td>true</td></tr><tr><td><code>min</code></td><td></td><td>false</td></tr><tr><td><code>max</code></td><td></td><td>false</td></tr><tr><td><code>errorMessage</code></td><td></td><td>false</td></tr></tbody></table>

#### Length

Validates that field's value for `String` column falls within `min` and `max` number of characters.

Either `min`, `max` or `both` must be defined. Values are inclusive.

<table><thead><tr><th>Name</th><th>Value</th><th data-type="checkbox">Is Required</th></tr></thead><tbody><tr><td><code>validate</code></td><td><code>length</code></td><td>true</td></tr><tr><td><code>min</code></td><td></td><td>false</td></tr><tr><td><code>max</code></td><td></td><td>false</td></tr><tr><td><code>errorMessage</code></td><td></td><td>false</td></tr></tbody></table>

#### Unique Across Multiple Fields

Validate uniqueness across multiple fields. To use it, place a `unique_with` validation on each field that you want to be part of the uniqueness validation, all sharing the same `uniqueKey`.

<table><thead><tr><th>Name</th><th>Value</th><th data-type="checkbox">Is Required</th></tr></thead><tbody><tr><td><code>validate</code></td><td><code>unique_with</code></td><td>true</td></tr><tr><td><code>uniqueKey</code></td><td></td><td>false</td></tr><tr><td><code>errorMessage</code></td><td></td><td>false</td></tr></tbody></table>

Here is an example set of fields using `unique_with` validations used to validate that the combination of `department code` and `employee Id`   fields are unique.

<pre class="language-json"><code class="lang-json"><strong>[
</strong>  {
    "key": "Department Code",
    "name": "Department Code",
    "type": "String",
    "validations": [
      {
        "validate": "unique_with",
        "uniqueKey": "Employee No"
      }
    ]
  },
  {
    "key": "Employee Id",
    "name": "Employee Id",
    "type": "Number",
    "validations": [
      {
        "validate": "unique_with",
        "uniqueKey": "Employee No"
      }
    ]
  }
]
</code></pre>

Here is the example of `unique_with` validation in action,

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption><p>Checking uniqueness of Employee No using unique_with validation</p></figcaption></figure>

## Adding Validations

### From Platform

1.  Click on `Validations` while adding column or click on `Edit` to edit the column.\


    <figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption><p>Mentioning Validations</p></figcaption></figure>
2.  Assign validations as needed,\


    <figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption><p>Assigning validations from web UI</p></figcaption></figure>

### From Code

You can check the advanced validations sections in react( [#advanced-validations](../importer/react-embed.md#advanced-validations "mention")), angular [#advanced-validations](../importer/angular-embed.md#advanced-validations "mention")) and javascript ([#advanced-validations](../importer/html-js-embed.md#advanced-validations "mention"))

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}

