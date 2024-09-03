---
description: >-
  If you are using a (currently) unsupported client framework, you can use our
  embedded script. This will show the Widget inside an iframe.
icon: js
---

# HTML & JS Embed

### Add Script

You copy this snippet to your code before the closing body tag.

{% code overflow="wrap" %}
```html
<script type="text/javascript" src="https://embed.impler.io/embed.umd.min.js" async></script>
```
{% endcode %}

It will add `impler` variable in `window`, so we can call its `init` and `show` methods later.

### Add Import Button

Import widgets get opened when the user clicks on `Import` button. So let's add an import button,

```markup
<button disabled id="impler-btn">
  Import
</button>
```

### Initialize Widget

Before the widget gets shown you have to call its `init` method. So write this code, after added `embed` script.

<pre class="language-javascript" data-line-numbers><code class="lang-javascript">&#x3C;script type="text/javascript">
  let uuid = generateUuid();
  let isImplerInitialized = false;
  const ImplerBtn = document.getElementById("impler-btn");

  function generateUuid() { // (1)
    return window.crypto.getRandomValues(new Uint32Array(1))[0];
  }

  window.onload = (e) => {
    if (window.impler) {
      window.impler.init(uuid); // (2)

      const readyCheckInterval = setInterval(() => {
        if (window.impler.isReady()) { // (3)
          clearInterval(readyCheckInterval);
          ImplerBtn.removeAttribute("disabled"); // (4)
        }
      }, 1000);

<strong>      ...
</strong>    }
  }
&#x3C;/script>
</code></pre>

Here is the description of what we just did,

1. `generateUuid` the function generates UUID which helps add multiple import widgets on the same page.
2. `init` method on impler initializes impler widget.
3. `readyCheckInterval` calls impler `isReady()` method in the interval of 1 second to check whether the impler widget is initiated or not.
4. Once `Impler` is ready we remove `disabled` attribute from the import button, which the user can click to open the import widget.

### Show Widget

After the initialization, when the user clicks on the Import button we will call `show` method to open the widget,

```javascript
// at #L21
ImplerBtn.addEventListener("click", (e) => {
  window.impler.show({
    uuid,
    projectId: "", // projectId
    templateId: "", // templateId
    accessToken: "", // accessToken
  });
});
```

You can pass more parameters to `show` a method like schema, data, etc. Have a look at [#props](react-embed.md#props "mention") section on React embed.

That's it, your app is now ready to onboard user data into your application.

### Customize Texts

You can customize any text in the import widget, here is the sample. A full list of available texts is available at [#available-texts](text-customization.md#available-texts "mention").

```html
ImplerBtn.addEventListener("click", (e) => {
  window.impler.show({
    ...
    texts: {
      STEPPER_TITLES: {
        REVIEW_DATA: 'Check Data', // New Title
      },
    },
  });
});
```

### Listening to Events

Impler instance provides `message` an event listener which gets called for various events happening with the widget. Here is how to attach event listener,

```javascript
window.impler.on('message', (eventData) => {}, uuid);
```

`eventData` follows the `{ type, value }` structure.

<table><thead><tr><th width="241">type</th><th width="146">value</th><th>Description</th></tr></thead><tbody><tr><td><code>UPLOAD_STARTED</code></td><td>UploadData</td><td>User has started import by selecting file and clicking on <code>See Mapping</code></td></tr><tr><td><code>UPLOAD_TERMINATED</code></td><td>UploadData</td><td>The user canceled the import in the middle of the import process.</td></tr><tr><td><code>UPLOAD_COMPLETED</code></td><td>UploadData</td><td>The user has completed the import.</td></tr><tr><td><code>CLOSE_WIDGET</code></td><td></td><td>The user has closed the import widget.</td></tr><tr><td><code>DATA_IMPORTED</code></td><td>ImportedData</td><td>Imported data has received on frontend.</td></tr></tbody></table>

### Complete Code Example

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Acme Inc</title>
  </head>
  
  <body>
    <button disabled id="btnOpenImpler">
      Import
    </button>
  
    <script type="text/javascript" src="https://embed.impler.io/embed.umd.min.js" async></script>
    <script type="text/javascript">
      let uuid = generateUuid();
      let isImplerInitialized = false;
      const EleBtnOpenImpler = document.getElementById("impler-btn");
  
      function generateUuid() {
        return window.crypto.getRandomValues(new Uint32Array(1))[0];
      }
  
      window.onload = (e) => {
        if (window.impler) {
          window.impler.init(uuid);
  
          const readyCheckInterval = setInterval(() => {
            if (window.impler.isReady()) {
              clearInterval(readyCheckInterval);
              EleBtnOpenImpler.removeAttribute("disabled");
            }
          }, 1000);
          
          EleBtnOpenImpler.addEventListener("click", (e) => {
            window.impler.show({
              uuid,
              projectId: "",
              templateId: "",
              accessToken: "",
              // Get these credentials from https://web.impler.io, (create import, add columns, got to "snippet", open "Add Import Button" to find credentials)
              // find out about more options here: https://docs.impler.io/widget/react-embed#props
            });
          });
          
          window.impler.on('message', (eventData) => {
            switch (eventData.type) {
              case "WIDGET_READY":
                console.log("Widget is ready");
                break;
              case "CLOSE_WIDGET":
                console.log("Widget is closed");
                break;
              case "UPLOAD_STARTED":
                console.log("Upload started", eventData.value);
                break;
              case "UPLOAD_TERMINATED":
                console.log("Upload skipped in middle", eventData.value);
                break;
              case "UPLOAD_COMPLETED":
                console.log("Upload completed", eventData.value);
                break;
              case "DATA_IMPORTED":
                console.log("Data imported", eventData.value);
                break;
              default:
                break;
            }
          }, uuid);
        }
      };
    </script>
  </body>
</html>
```

### [Data Seeding](../features/data-seeding.md) in Sample File

You can provide default data to fill in the Sample Excel file that gets generated from the Import widget. Default data act as a placeholder for the user to further add or update the data in the file.

Here is an example of how to provide data to fill in the sample file,

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  data: [
    { country: 'ABC' },
    { country: 'DEF' },
    { country: 'GHE' },
  ]
});
```

### Providing [Runtime Schema](../features/runtime-schema.md)

The schema and output provided in the [web.impler.io](https://web.impler.io) portal for any import behave as default values for any Import. It's possible to override the default schema and output, to adapt dynamic nature of Import.

Here is an example of how to provide dynamic schema and output,

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  schema: [
    {
      key: 'country',
      name: 'Country',
      type: 'String'
    }
  ],
  output: {
      "%data%": {
        "country_id": "{{country}}"
      },
      "page": "{{page}}",
      "chunkSize": "{{chunkSize}}",
      "isInvalidRecords": "{{isInvalidRecords}}",
      "template": "{{template}}",
      "uploadId": "{{uploadId}}",
      "fileName": "{{fileName}}",
      "extra": "{{extra}}"
    }
});
```

### Passing Extra Parameters

It's an obvious need that we want to pass `userId` or `orgId` representing who imported the data. In that case, you can pass that data in an extra parameter.

You can pass `string`, `object`, or `array` in extra. Here is an example of how to do it,

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  extra: {
      userId: '4ddhodw3',
      time: new Date()
  }
});
```

The extra parameters get sent to an application during the webhook call.

### Changing Import Title

By default, the Import widget takes the name of the Import to show in the title. But it's possible to change the `title` from the implementation side too. Helpful to keep the title separate from what the name is given in the web portal.

Here is how,

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  title: "Employee Import"
});
```

### Programmatically Closing the Import Widget

You can close the import widget programmatically by calling `close` method on impler instance,

Here is how,

```javascript
window.impler.close();
```

### Changing Theme Color

You can pass a primary color to the import widget, which will update the colors of all buttons accordingly to match your app's theme color.

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  primaryColor: '#5f45ff'
});
```

### Providing Authentication Header Value

In case the backend endpoint is authenticated with the token, it's possible to provide token value from the implementation side.

```javascript
window.impler.show({
  uuid,
  projectId: "",
  templateId: "",
  accessToken: "",
  authHeaderValue: '...'
});
```

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
