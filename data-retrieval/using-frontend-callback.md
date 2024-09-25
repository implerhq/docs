---
description: >-
  Get sanitized and formatted user-imported data Directly on your frontend
  application. Helping you to access data directly.
---

# 💠 Using Frontend Callback

{% hint style="info" %}
Available from @impler/react@0.21.0 SDK. Not advisable to access imported data on the front end, if importing more than 10K records.
{% endhint %}

Once the user completes importing the spreadsheet in the widget, you access imported data immediately on the frontend application.

## Enable Frontend Callback Destination

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption><p>Steps to enable frontend callback </p></figcaption></figure>

1. Open the Import and go to the `Destination` section.
2. Enable `Get Imported Data in Frontend`.

## Get Imported Data on Frontend

Once the destination is enabled Impler will start sending Imported data on the frontend.

To access we can use `onDataImported` method at [#listening-for-events](../importer/react-embed.md#listening-for-events "mention") if using react or can check for a`DATA_IMPORTED` event as per [#listening-to-events](../importer/html-js-embed.md#listening-to-events "mention") if using HTML & JavaScript.

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
