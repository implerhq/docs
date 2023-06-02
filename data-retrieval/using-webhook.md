---
description: Get data right into the application whenever the user imports the spreadsheet
---

# 🪝 Using Webhook

Once the user completes importing the spreadsheet in the widget, the impler starts sending spreadsheet data to the callback URL mentioned in the **project**.

If the callback URL is protected, there is a facility to add **header-based authentication**. To activate it you can mention `authHeaderName` in the **project** and its value to the `import` button as `authHeaderValue` prop.

Data will be sent to the application in chunks, you can mention your desired `chunkSize` in **project**.

Data will be sent to the `callbackURL` in the following format,

<table><thead><tr><th>Name</th><th data-type="select" data-multiple>Type</th><th>Description</th></tr></thead><tbody><tr><td>template</td><td></td><td><code>CODE</code> of the template</td></tr><tr><td>uploadId</td><td></td><td>Upload ID</td></tr><tr><td>data</td><td></td><td>Array of data in JSON format</td></tr><tr><td>totalRecords</td><td></td><td>Total number of records in uploaded spreadsheet</td></tr><tr><td>totalPages</td><td></td><td>Total number of pages the data is divided on</td></tr><tr><td>page</td><td></td><td>Current page number</td></tr><tr><td>pageSize</td><td></td><td>Size of the data being sent</td></tr><tr><td>extra</td><td></td><td>Extra string or JSON if it's being passed to <code>Import</code> button</td></tr><tr><td>isInvalidRecords</td><td></td><td>If current records are invalid records</td></tr></tbody></table>
