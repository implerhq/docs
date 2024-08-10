---
description: >-
  Impler allows importing data files with images. Image import is useful in
  scenarios like Employee data with profile photos, Products with images, or
  Assets with pictures.
---

# 📸 Import with Image

Image Upload feature is available in the Scale plan only! Feel free to [reach out](https://discord.impler.io) in case you want to try it out!

### How do I enable Image upload in Import?

The first step for image import is to add or update a column with the `Image` type. In case providing [runtime-schema.md](runtime-schema.md "mention") keep column type as `Image` and importer will be ready to import images.

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption><p>Add Column with Type Image</p></figcaption></figure>

### How does Image Import work?

Once the import is configured to import data with Image. We can start importing data with Images. Here is the image import flow,

#### 1. Generate a Template with Images,

The first step is to upload all images and generate a template with uploaded image names. All columns with the type Image will appear in `Select Column` dropdown and Uploaded images will be shown below `Upload Image` section.

Once all image files are selected, click on `Generate Template` to generate excel file holding names of all uploaded images.

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption><p>Upload Images and Generate Template</p></figcaption></figure>

#### 2. Upload Excel with data and image names.

Clicking on Generate Template will download an Excel file and Importer will move to the Upload section. You can enter data in the downloaded Excel file and select image names for image columns.

It's possible to generate template again by clicking on `Generate Template`.

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption><p>Upload data file with image cell values</p></figcaption></figure>

Once selected click on `Map Columns`.

#### 3. Do mapping for columns

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption><p>Do and verify mapping for columns</p></figcaption></figure>

Click on `Review Data` to verify data getting imported.

#### 4. Review Data

The review step checks if image columns contain the name of the uploaded image. If not shows a validation error.

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption><p>Review data getting imported</p></figcaption></figure>

Click on `Re-Review Data` to complete the import, once all records are valid.

#### 5. Complete Import

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption><p>Data Imported Confirmation</p></figcaption></figure>

#### 6. Get Imported Data

Imported data will be sent to a webhook with an endpoint to download and access the uploaded file. &#x20;

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption><p>Import Webhook Response</p></figcaption></figure>

#### 7. Download or Access the uploaded file

The download file endpoint is secured using `accesskey` which is available in `Settings` section on the left side. Here is the CURL for a review,

```
curl --location --request GET 'https://api.impler.io/v1/upload/66b759d087a854c817cd3e98/asset/logo-icon.png' \
--header 'accesskey: <ACCESS_TOKEN>'
```

***

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
