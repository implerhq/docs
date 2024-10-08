---
description: >-
  No need to download Excel, do mapping, review, and complete import. Directly
  write data into the importer and finish your import in just one step.
icon: pen-circle
---

# Directly Enter your Data

### Normal Flow

The normal importer flow has a higher number of steps to import the file and follows the below structure,

1. Download Sample File.
2. Write data into the file using spreadsheet editing software like Excel, Libre Office Calc, Numbers, etc.
3. Upload the file in which data is entered.
4. Select the header row.
5. Map columns.
6. Review data and fix invalid data if there is any.
7. Complete the Import.

This process takes a lot of time and involves many steps in the data import process. We introduced the facility to "Directly enter your data" to reduce the time and effort required to complete the import.

### Directly enter your data

*   Open the Importer and click on `Directly enter your data`.\


    <figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Click on "Directly Enter your Data"</p></figcaption></figure>
*   The spreadsheet editor will be opened which will show the column names as header and as per column types, columns will be shown. For example, for the date column, a date picker will be shown.

    <figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>Direct Expenses Data Entry</p></figcaption></figure>
* Data will be validated instantly, so you can just continue editing the data and the importer will continue validating it in the background.
* While pasting the data directly from the spreadsheet, the validation will be performed after pasting is done.
* The user can not Finish Import if the data contains invalid values.
* On finish the data will be sent to frontend ([using-frontend-callback.md](../data-retrieval/using-frontend-callback.md "mention")), Webhook ([using-webhook.md](../data-retrieval/using-webhook.md "mention")), or Bubble ([bubble.io-embed.md](bubble.io-embed.md "mention")) as per the destination.

{% synced-block url="https://app.gitbook.com/o/yCmyE3hFyolSGBXaxT9T/blocks/syb_1dWvX" %}
[Your feedback is crucial in...](https://app.gitbook.com/o/yCmyE3hFyolSGBXaxT9T/blocks/syb\_1dWvX)
{% endsynced-block %}
