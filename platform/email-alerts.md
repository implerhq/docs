---
description: >-
  Impler will send you alert mail for anything that goes wrong during importing
  data
icon: paper-plane
---

# Email Alerts

We heard issues like "I imported data but didn't receive callback", "Imported data is not showing in my application", "Validation code is not working as expected", etc. Also, "imported data not seen in the application", is something no one wants to face.

As a solution, Impler will send alert mail to users in the following scenarios,

1. Added webhook endpoint is not proper.
2. Application threw an error while sending imported data over the webhook.
3. Validation code throws an error during execution, which happens when data import is in progress.

Here is the sample mail,

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption><p>Sample mail sent to user while validation code fails</p></figcaption></figure>

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
