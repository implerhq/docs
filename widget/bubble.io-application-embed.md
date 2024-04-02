---
description: >-
  Enjoy the benefits of a readymade CSV Excel import experience in your
  application with bubble's no-code development platform.
---

# 🫧 Bubble.io Application Embed

## 1. Setting Bubble App

{% hint style="info" %}
**You must have a paid bubble application plan** to use the Bubble Data API, which is necessary to push external data into the Bubble data store.
{% endhint %}

### **i. Setting up data type**

Prepare a data type in your Bubble app where you want to push the CSV data. Ensure that the data type is `Publicly visible`. Add custom fields to the data type as per your requirements.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Important:** Manually add at least one entry to the data type to map columns accurately.
{% endhint %}

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>Making sure that at least one entry is exist in datatype</p></figcaption></figure>

### **ii. API Settings**

1. Go to Settings :gear:
2. Go to the **API** tab
3. Click on **Enable Data API**
4. Activate API for the data type where you want to push the imported data
5. Generate the API **Private Key** and save it.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>API Settings for Importing Data</p></figcaption></figure>

## 2. Setting up the Impler Application

Visit [web.impler.io](https://web.impler.io) and log in.

### i. Click on the "Create Import" button to get started with the new import

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Click on "Create Import" button</p></figcaption></figure>

### ii. Write an appropriate name and click on "Create & Continue"

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

#### iii. Enable bubble destination and fill in the details

Go to the destination tab and enable Bubble.io. You will have to fill in the following information, Bubble App Name:&#x20;

* **Bubble App Name** - This is the name of your Bubble.io app, in most cases it's available in a URL like <mark style="color:blue;">https://bubble.io/page?name=index\&id=impler-app\&tab=tabs-1</mark>, in which `impler-app` is the id.
* **Custom Domain Name** - Provide the address of the domain name like <mark style="color:blue;">example.com</mark> if you have attached any custom domain to your application.
* **Environment** - Pick from a development or production environment, based on which environment your app is running on.
* **API Private Key** - It is the API token that you have generated while configuring the [#ii.-api-settings](bubble.io-application-embed.md#ii.-api-settings "mention") Bubble app.
* **Data Type** - The name of the data type where data will be sent.

Once done click on **Test and Save**, which will check details with bubble.io and save the data.

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption><p>Bubble app configuration</p></figcaption></figure>

#### iv. Map Columns

Click on **Map Columns** to automatically map fields from bubble data type to Impler.

{% hint style="info" %}
Impler adds **user: \{{extra.userId\}}** field to output considering you want to keep track of who is importing data. Which you can remove from **5. Output** tab if you don't need the userId field.
{% endhint %}

## 3. Using the Plugin

### i. Install plugin

The last step is to add a readymade import plugin to your application.

1. Go to Plugins and click on **Add Plugins**
2. Search for **CSV Excel Import Plugin**
3. Click on **Install**

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>CSV Excel Import Plugin by Impler on Bubble.io</p></figcaption></figure>

### ii. Use Plugin

Now use the drag and drop Import Button element from the UI panel to add the Import button in the application.

1. **Project Id** - Project from which import is happening
2. **Template Id** - Import Id in which data is getting imported
3. **Access Token** - Security token used to authenticate communication.
4. **Primary Color** - Change the color theme of the import widget by selecting the color of your application.
5. **User Id** - Provide the User ID of the current user importing data into the application.

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

&#x20;Project Id, Template Id, and Access Token are found in the **Destination** section of the application.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Once done CSV & Excel Import functionality is ready in your application. If you face any issues you can chat with us using 💬 box in the bottom left corner.
