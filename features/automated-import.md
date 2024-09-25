---
icon: robot-astromech
description: >-
  Impler allows facility to automate data import from remote locations. Data
  import from remote locations makes it easy when data needs to be imported
  automatically without human intervention.
---

# Automated Import

{% hint style="info" %}
Automated Import feature is available in the Scale plan only! Feel free to [reach out](https://discord.impler.io) in case you want to try it out!
{% endhint %}

### How do I enable the automated import feature?

The process of automatic data import looks the same as manual data import, where the user uploads a file and impler imports the data. To convert any import to automated import we just need to switch its mode from `Manual` to `Automatic`. Once done your import is transformed from `Manual` to `Automatic` Import Mode.

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption><p>Automatic Import</p></figcaption></figure>

### How does Automated Import work?

When we switch import mode to Automatic, the Import widget gets transformed and instead of accepting the file from the user, the import widget asks the user for a source from where data will get imported on interval.

At the moment impler accepts `RSS URL` as a source from where data will be fetched at user-specified intervals. The embed process of automatic import is the same as manual import. Here is how automatic import works:

#### Step 1: Configure

The first step is to provide a source from where data will be imported at regular intervals. Here on RSS URL input, the user can provide the RSS URL and Impler will keep importing data from the URL.

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption><p>Configure Source of Automatic Import</p></figcaption></figure>

#### Step 2: Map Columns

The second step is to Map appropriate columns from the RSS file. As RSS follows XML structure, Impler parses the RSS file, extracts all paths for possible values in the XML file, and returns headings. Users can pick an appropriate heading for the column.

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption><p>User mapping XML fields with columns</p></figcaption></figure>

#### Step 3: Schedule Timing

Impler imports data from specified sources at regular intervals. In the schedule step user defines the Interval. The ability to specify intervals in Minutes, Hours, Days, Months, and Days makes it limitless for a user to provide any timing.

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption><p>Specifying the interval of automated import</p></figcaption></figure>

#### Step 4: Confirm

At the end, impler confirms the automated import configuration. Which shows the source and when it will run.

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption><p>Confirming Automated Import</p></figcaption></figure>

#### Automated Imports are associated with users

Automated imports are associated with users. Users referred to here are users of end application who uses Impler. To mention userId we have to provide `externalUserId` extra parameters. As mentioned in [#passing-extra-parameters](../importer/react-embed.md#passing-extra-parameters "mention") (React) and [#passing-extra-parameters](../importer/html-js-embed.md#passing-extra-parameters "mention") (HTML & JS).

You can provide anything in `externalUserId`. ID or Email address that uniquely identifies the user is best suitable for value in `externalUserId`.

### Showing Automated Imports in Application

Automated Imports refers to the user. It becomes obvious to show users import jobs into your application. Here are all the APIs to deal with import jobs in Impler.

#### Getting User Import Jobs

{% code overflow="wrap" %}
```
curl --location --request GET 'https://api.impler.io/v1/import-jobs/user/:externalUserId' \
--header 'accesskey: <ACCESS_TOKEN>'
```
{% endcode %}

#### Pause the User Import Job

{% code overflow="wrap" %}
```
curl --location --request GET 'https://api.impler.io/v1/import-job/user/:jobId/pause' \
--header 'accesskey: <ACCESS_TOKEN>'
```
{% endcode %}

#### Resume the User Import Job

{% code overflow="wrap" %}
```
curl --location --request GET 'https://api.impler.io/v1/import-job/user/:jobId/resume' \
--header 'accesskey: <ACCESS_TOKEN>'
```
{% endcode %}

#### Delete the User Import Job

```
curl --location --request GET 'https://api.impler.io/v1/import-job/user/:
externalUserId/:jobId' \
--header 'accesskey: <ACCESS_TOKEN>'
```

***

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
