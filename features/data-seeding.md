---
description: >-
  Populate essential data fields in your Excel samples with Data Seeding.
  Simplify data input by preloading records, allowing users to build upon or
  modify data.
---

# 🗃️ Data Seeding

{% hint style="info" %}
Available after impler version `0.9.1`&#x20;
{% endhint %}

To seed the file that gets downloaded as `Sample`, one need to pass `data` in `showWidget` function, which is exported from the `useImpler` hook.

This function, when provided with your data, allows Impler to automatically populate sample files with the specified information.

Here is how to do it,

```jsx
import { useImpler } from '@impler/react';

const { showWidget, isImplerInitiated } = useImpler({
    projectId: "...",
    templateId: "...",
    accessToken: "...",
});

function onShowWidgetClick = () => {
    // Fetch or generate your data from a relevant source
    let data = [ /* Your data here */ ];
    showWidget({ data });
}

<button disabled={!isImplerInitiated} onClick={onShowWidgetClick}>
    Import
</button>
```

## Using the \`showWidget\` Function

1. **Import the `useImpler` Hook:** Start by importing the `useImpler` hook from `@impler/react` into your project. This hook provides access to essential Impler functions.
2. **Initialize Impler**: Create an instance of Impler by calling `useImpler` with the required configuration, including `templateId`, `projectId`, and `accessToken`.
3. **Define Your Data**: In the `onShowWidgetClick` function, gather the data you want to prefill into the sample file. This data should match the structure and content you expect in the final imported files.
4. **Call `showWidget`**: Pass your data to the `showWidget` function, which will handle the process of populating the sample files.
5. **Downloading sample file with data**: Finally, when user clicks on button with text `Import`, the Import widget gets opened. Where by clicking on `Download sample` the user can download the excel file with data provided.

## Benefits at a Glance

* **Efficient Data Import**: Simplify the process of importing relational data by seeding sample file.
* **Developer-Friendly**: Integrate data sources seamlessly into Impler's import workflow.
* **User-Focused**: Enhance the user experience by providing prepopulated sample files for download.

With the Data Seeding feature in Impler, you can save time and effort by automating the generation of sample files.

This is particularly valuable when importing data with complex relationships, ensuring a smooth and efficient data import experience.

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
