---
icon: b
description: >-
  Add readymade, scalable, and powerful CSV Excel import experience in your
  Bubble.io application.
---

# Bubble.io Embed

## 1. Setting Bubble App

{% hint style="info" %}
**You must have a paid bubble application plan** to use the Bubble Data API, which is necessary to push external data into the Bubble data store.
{% endhint %}

### **i. Setting up data type**

Prepare a data type in your Bubble app where you want to push the CSV data. Ensure that the data type is `Publicly visible`. Add custom fields to the data type as per your requirements.

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Important:** Manually add at least one entry to the data type to map columns accurately.
{% endhint %}

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption><p>Making sure that at least one entry is exist in datatype</p></figcaption></figure>

### **ii. API Settings**

1. Go to Settings :gear:
2. Go to the **API** tab
3. Click on **Enable Data API**
4. Activate API for the data type where you want to push the imported data
5. Generate the API **Private Key** and save it.

<figure><img src="../.gitbook/assets/image (10) (1).png" alt=""><figcaption><p>API Settings for Importing Data</p></figcaption></figure>

## 2. Setting up the Impler Application

Visit [web.impler.io](https://web.impler.io) and log in.

### i. Click on the "Create Import" to create the new import

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p>Click on "Create Import" button</p></figcaption></figure>

### ii. Give name and click on "Create & Continue"

<figure><img src="../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>Give appropriate name in create Import for</p></figcaption></figure>

### iii. Enable Bubble.io destination

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Bubble app configuration</p></figcaption></figure>

Go to the destination tab and enable Bubble.io. Fill in the following information,

* **Bubble App Name** - This is the name of your Bubble.io app, in most cases it's available in a URL like <mark style="color:blue;">https://bubble.io/page?name=index\&id=impler-app\&tab=tabs-1</mark>, in which `impler-app` is the id.
* **Environment** - Pick from a _development_ or _production_ environment, based on which environment your app is running on.
  * **Custom Domain Name** - If the environment is _production_, provide a domain name address like <mark style="color:blue;">example.com</mark> if you have attached any custom domain to your application.
* **API Private Key** - It is the API token that you have generated while configuring the [#ii.-api-settings](bubble.io-embed.md#ii.-api-settings "mention") Bubble app.
* **Data Type** - The name of the data type where data will be sent.

Once done click on **Test and Save**, which will check details with bubble.io and save the data.

### iv. Map Columns

Click on **Map Columns** to automatically map fields from bubble data type to Impler.

## 3. Using the Plugin

The last step is to add a CSV Excel Import plugin to your application.

### i. Install plugin

1. Go to Plugins and click on **Add Plugins**
2. Search for **CSV Excel Import Plugin**
3. Click on **Install**

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>CSV Excel Import Plugin by Impler on Bubble.io</p></figcaption></figure>

### ii. Using the Plugin

Now go to the Design panel (1) and search for _CSV Excel Importer (2)_ which is available in the _Visual Elements_ Section. Drag and drop Importer on the UI panel. It doesn't have any visuals so we can hide (3) it.

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption><p>Adding Importer on UI</p></figcaption></figure>

#### a. Initialize Importer on Page Load

Go to workflow panel (1). Click on _Add Event_ and add _Page Load_ event (2). For the added event add _Initialize Import Widget_ action, which is available in _Element Actions (3)_.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption><p>Workflow Initialize Importer on Page Load</p></figcaption></figure>

#### b. Add a Button on the Page and Add Workflow

From the design section add Button (1), which will open its properties from there click on _Add Workflow_.

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p>Add Button and Workflow</p></figcaption></figure>

#### c. Add Workflow to Open Importer on Button Click

From workflow panel (1), for Button (2) add the _Open Import Widget_ action.&#x20;

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption><p>Open Import Widget on Button Click</p></figcaption></figure>

#### d. Configure Importer

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption><p>Configuring Importer with Credentials from Impler Application</p></figcaption></figure>

&#x20;Project Id, Template Id, and Access Token are found in the **Snippet** section of the application.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption><p>Getting credentials from Impler portal for Bubble Plugin</p></figcaption></figure>

Once done CSV & Excel Import functionality is ready in your application.

## 4. Considering UserId while importing data

### i. Configuring import plugin to consider UserId

The impler import plugin provides a field for **User Id**, where one can provide static text or dynamic value as User ID. It's optional. Very useful while adding a relationship with the user.

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

### ii. Passing userId to Bubble.io when data is imported

If you're taking static or dynamic userId field, you have to append `"user": {{extra.userId}}` in output schema.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption><p>Adding userId in output format</p></figcaption></figure>

Here **user** is the field name in Bubble.io. You need to follow the name you have in your Bubble.io application.

## 5. Theming Importer

Provide Primary Color in properties to change the color theme of Importer.

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption><p>Providing Primary Color to the Importer</p></figcaption></figure>

## 6. Configuring multiple Importers on Page

> In Progress

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
