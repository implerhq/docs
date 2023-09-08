---
description: >-
  Write your own validation code, making it possible to perform complex checks,
  such as validating data against external databases or APIs.
---

# 🦄 Custom Validation

{% hint style="info" %}
Available after impler version `0.9.1`&#x20;
{% endhint %}

To implement custom validation logic, you can use the code editor provided in the `Validator` tab of the Import Details page.

Your custom validation function should adhere to this structure:

```javascript
exports.code = async (params) => {
    let errorRecords = [];
    // Your custom validation logic here
    return errorRecords;
}
```

The `code` function must have the name `code`, and it can return an array of error records if validation failures occur. Impler will call this `code` function when performing custom validation.

## Parameters provided to the \`code\` Function

The `params` object provided to your custom validation function contains essential information about the import process and the data being validated. It follows this structure:

```json5
{
    uploadId: string;
    extra: string | number | json;
    fileName: string;
    data: [
        {
            index: number;
            record: {
                [key: string]: string | number;
            };
            errors: {};
            isValid: boolean;
        }
    ];
    totalRecords: number;
    chunkSize: number;
}
```

* `uploadId` is the id of import happening at the moment.
* `extra` is the `string`, `number` or `json` provided at the time of import.
* `fileName` is the name of file that is being imported.
* `data` is the array of records, where each record follows this strcuture:
  * `index` of the record
  * `record` the actual record object being imported
  * `errors` is an key-value pair of errors for key of `record` if there is any
  * `isValid` flag indicating whether current record has errors or not
* `totalRecords` number indicating totalRecords being imported
* `chunkSize` number indicating current size of records

## Returned Error Records

Error records returned from your custom validation code should follow this structure:

```
[
    { 
        index: 1, 
        errors: {
            email: 'Email is already in use.'
        } 
    }
]
```

In the case of all records passing validation, return an empty array `[]`.

## Example, Validating data against database data

Here's an example of how to validate data against data from a database using the Axios library:

```javascript
const axios = require('axios');

exports.code = async (params) => {
  let errorRecords = [];
  let users = await axios.get('https://your-api.com/users');
  let userEmails = users.map(user => user.email);
  
  for(let item of params.data) {
    let error = {
      index: item.index,
      errors: {},
    }
    if(userEmails.includes(item.email)) {
      errors['email'] = "Email must be unique."
    }
    errorRecords.push(error);
  }
  return errorRecords;
}

```

## Features

### Access to variables inside code editor

Developers can access schema keys by pressing `Ctrl + Space` to display a list of available variables and selecting from it.

Additionally, the suggestion box contains variables available in `params`, such as `params.uploadId`, `params.fileName`, and more.

### Performing HTTP calls

Your custom validation code can make HTTP calls using libraries like Axios. For example, you can retrieve data from your own API and validate it against the imported data.

### Validation execution in chunks

The custom code function is executed in chunks, typically in batches of 500 records.

For example, if you are validating 10,000 records, the function will be called 20 times to validate the data in manageable segments.

### Combining with static validation

Error records generated from your custom validation code are merged with errors generated from Impler's static validation processes, creating a comprehensive error report.

### Scalable Architecture

Impler's custom validation functionality is built on a scalable architecture, allowing you to handle and validate large datasets, even in the millions.



With custom validation in Impler, you have the flexibility to implement intricate validation logic, ensuring data integrity and quality in your import processes.

This feature empowers you to customize your imports to meet your specific needs, making complex data imports more accessible and efficient.
