---
description: >-
  Want to let your users easily import data from spreadsheets directly into your
  Bubble application? Impler provides a smooth, user-friendly data import
  experience. This guide will walk you through inte
icon: b
---

# Bubble.io Embed

**Before You Start: Prerequisites**

{% hint style="info" %}
1. **Bubble Paid Plan:** You **must** have a paid Bubble plan. The Bubble Data API, which Impler uses to push data, is only available on paid plans.
2. **Impler Account:** You'll need an account with Impler. Sign up or log in at [web.impler.io](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fweb.impler.io).
{% endhint %}

### **i. Prepare Your Bubble App**

First, we need to set up the data structure in Bubble and enable the API for Impler to connect.

1. **Go to Data Tab:** In your Bubble editor, navigate to the "Data" tab.
2. **Select Data Types:** Ensure you have the "Data types" sub-tab selected.
3. **Define/Verify Your Data Type:**
   * Identify the Data Type you want to import data into (e.g., Employees, Products, Contacts).
   * Make sure this Data Type has all the necessary fields you want to import (e.g., Full Name (text), Email (text), Date of Birth (date), Social Security Number (text)). Create any missing fields using the "Create a new field" button.
   * **Crucially:** This Data Type **must** be set to `Publicly visible`. Impler needs this permission to see the structure. Check the privacy rules for this data type if needed, but the type definition itself needs to be discoverable.

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Important:** Add at least one entry (row) manually to this data type.
{% endhint %}

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption><p>Making sure that at least one entry is exist in datatype</p></figcaption></figure>

### **ii. Enable Bubble Data API & Get Key**

1. **Go to Settings Tab:** Navigate to the `Settings` tab in your Bubble editor.
2. **Go to API Sub-Tab:** Click on the `API` sub-tab.
3. **Enable Data API:** Scroll down to the `Public API endpoints` section. Check the box labeled `Enable Data API`.
4. **Expose Your Data Type:** In the list below `Enable Data API`, find the Data Type you prepared in Step 1.1 (e.g., Employees) and **check the box next to it**. This allows API access specifically for this data type.
5. **Generate API Private Key:** Scroll further down to "API Tokens".
   * Enter a descriptive label for your key (e.g., "Impler Key").
   * Click "Generate a new API token".
   * Bubble will generate a **Private key**. **Copy this key immediately** and save it somewhere secure. You will need it shortly, and Bubble won't show it to you again.

<figure><img src="../.gitbook/assets/image (10) (1).png" alt=""><figcaption><p>API Settings for Importing Data</p></figcaption></figure>

## 2. **Set Up Your Import Project**

Now, let's configure Impler to receive data and send it to your Bubble app.

### 2.1) **Create an Import**

1. **Log in to Impler:** Go to [web.impler.io](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fweb.impler.io) and log in.
2. **Create New Import:** Click the `Create Import` button.
3. **Name Your Import:** Give it a clear name (e.g., "Bubble Employees Import") and click `Create & Continue`

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p>Click on "Create Import" button</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>Give appropriate name in create Import for</p></figcaption></figure>

### 2.2) **Configure Bubble.io as the Destination**

1. **Go to Destination Tab:** Inside your newly created import, click on the `Destination` tab.
2. **Enable Bubble.io:** Find the "Bubble.io" option and toggle it **ON**.
3. **Fill in Bubble App Details:**
   * **Bubble App Name:** Enter the name of your Bubble app. This is the part before `.bubbleapps.io` in your app's URL (e.g., if your app is mycoolapp.bubbleapps.io, enter mycoolapp).
   * **Environment:** Choose production (for your live app) or development (for your test version).
   * **Custom Domain Name (Optional):** If your app uses a custom domain (e.g., app.mycompany.com), enter it here. Otherwise, leave it blank.
   * **API Private Key:** Paste the **Private key** you generated and saved from Bubble (Step 1.2).
   * **Datatype Name:** Enter the **exact name** of the Bubble Data Type you prepared (e.g., Employees). Case-sensitivity might matter, so match it precisely.
4. **Test and Save:** Click "Test and Save". Impler will attempt to connect to your Bubble app using the details provided. Fix any errors if they occur.

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Bubble app configuration</p></figcaption></figure>

### 2.3) **Map Columns (Automatic)**

1. **Click "Map Columns":** After saving the destination, click the "Map Columns" button (often located near the Bubble.io destination settings).
2. **Auto-Mapping:** Impler will attempt to automatically detect the fields from your Bubble Data Type and map them. Review the mappings to ensure they look correct. You can typically adjust these mappings later in the main Impler schema editor if needed.

## 3. **Install the Impler Plugin**

Let's add the importer interface to your Bubble app.

### 3.1) **Install the Impler Plugin**

1. **Go to Plugins Tab:** In your Bubble editor, go to the "Plugins" tab.
2. **Add Plugins:** Click the "+ Add plugins" button.
3. **Search:** Search for "CSV Excel Import Plugin Impler".
4. **Install:** Find the correct plugin and click "Install", then "Done".

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>CSV Excel Import Plugin by Impler on Bubble.io</p></figcaption></figure>

### 3.2) **Add the Impler Element to Your Page**

1. **Go to Design Tab:** Navigate to the page where you want the import button/functionality.
2. **Find Impler Element:** In the "Visual Elements" section on the left panel, find "CSVExcelImporter" (the name might vary slightly based on the plugin version).
3. **Drag onto Page:** Drag and drop this element onto your page. **Note:** This element is usually invisible to the end-user; it just provides the necessary functions. You can place it anywhere, even outside the visible page area if you prefer.

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption><p>Adding Importer on UI</p></figcaption></figure>

### **3.3) Get Your Impler Project Credentials**

1. **Go Back to Impler:** Return to your Impler project ([web.impler.io](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fweb.impler.io)) and open the importer.
2. **Click Integrate:** Find and click the `Integrate` button (in the top-right of your Importer).
3. **Copy Credentials:** A modal or section will appear showing:
   * `projectId`
   * `templateId`
   * `accessToken`\
     Copy these three values.

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption><p>Click on <code>Integrate</code> to open the integration modal</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption><p>Get the <code>ProjectId</code>, <code>TemplateId</code> and <code>Access Token</code></p></figcaption></figure>

### **3.4) Configure the Impler Element in Bubble**

1. **Select Impler Element:** Back in your Bubble editor (Design tab), double-click the CSVExcelImporter element you added in Step 3.2 to open its properties editor.
2. **Paste Credentials:** Paste the projectId, templateId, and accessToken you copied from Impler into the corresponding fields in the element's properties panel.

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption><p>Configuring Importer with Credentials from Impler Application</p></figcaption></figure>

### **3.5) Initialize the Importer (Workflow)**

We need to tell the Impler element to get ready when the page loads.

1. **Go to the Workflow Tab:** In your Bubble editor, switch to the "Workflow" tab.
2. **Create Page Load Event:** Click "Click here to add an event..." and choose "General" -> "Page is loaded".
3. **Add Initialize Action:** Click "Click here to add an action...", choose "Element Actions" -> "Initialize Importer" (the action name might vary slightly, select the one related to your CSVExcelImporter element).
4. **Select Element:** In the action properties, make sure the correct CSVExcelImporter element is selected.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption><p>Workflow Initialize Importer on Page Load</p></figcaption></figure>

#### 3.6) **Trigger the Importer (Workflow)**

Users need a way to open the importer, typically via a button.

1. **Add a Button:** Go back to the "Design" tab and add a standard Bubble Button element to your page. Label it something like "Import Data" or "Upload CSV".
2. **Add Button Workflow:** Select the button and click "Start/Edit workflow".
3. **Add Open Widget Action:** Click "Click here to add an action...", choose "Element Actions" -> "Open Import Widget" (again, select the action associated with your CSVExcelImporter element).
4. **Select Element:** Ensure the correct CSVExcelImporter element is selected in the action properties.

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p>Add Button and Workflow</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption><p>Open Import Widget on Button Click</p></figcaption></figure>

{% hint style="success" %}
**You're ready to test!** Preview your Bubble page. Clicking the "Import Data" button should now open the Impler import widget, ready for your users to upload their files.
{% endhint %}

## 4. **Optional Advanced Configuration**

### **4.1: Associating Imported Data with a User (UserId)**

If you want to link the imported data to the specific Bubble user who uploaded it (e.g., storing the user on each imported Employee record):

1.  **In Bubble (Plugin Element):**

    * Select the CSVExcelImporter element in the Design tab.
    * In its properties, find the User Id field.
    * Use Bubble's dynamic data capabilities to insert the relevant user ID. This is often Current User's unique id.

    <figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption><p>Configuring User Id</p></figcaption></figure>
2.  **In Impler (Destination Output):**

    * Go to your Impler project settings -> Destination tab.
    * Find the output schema or transformation settings (this might look like a code editor).
    * You need to tell Impler to include the User ID it receives from the plugin. Add a field mapping like this: "user": "{extra.userId}" (or potentially "Creator": "{extra.userId}" if your Bubble field is named Creator and is of type User). The exact syntax might depend on Impler's current interface, but the principle is to map the incoming extra.userId to the correct Bubble User field. **Important:** The field name on the left (user or Creator) MUST match the field name in your Bubble Data Type that holds the user information.

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption><p>Adding userId in output format</p></figcaption></figure>

### 4.2) **Customizing Importer Appearance (Theming)**

1. **In Bubble (Plugin Element):**
   * Select the CSVExcelImporter element in the Design tab.
   * In its properties, find the Primary Color field.
   * Set a hex color code (e.g., #FF0000 for red) to customize the theme of the Impler widget to match your app's branding.

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption><p>Providing Primary Color to the Importer</p></figcaption></figure>

That's it! You've now integrated the Impler data importer into your Bubble application. Your users can now benefit from a streamlined way to upload data via CSV or Excel files. Remember to test thoroughly with different file types and data variations.

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}
