---
description: >-
  If you are using a (currently) unsupported client framework, you can use our
  embedded script. This will show the Widget inside an iframe.
---

# 🪄 HTML & JS Embed

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

Before the widget gets shown you have to call its `init` method. So write this code to after adding `embed` script.

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

## Show Widget

After the initialization, when the user clicks on the Import button we will call `show` method to open the widget,

```javascript
// at #L21
ImplerBtn.addEventListener("click", (e) => {
  window.impler.show({
    uuid,
    templateId: "", // templateId
    projectId: "", // projectId
    accessToken: "", // accessToken
  });
});
```

You can pass more parameters to `show` method like schema, data, etc. Have a look at [#props](react-embed.md#props "mention") section on React embed.

That's it, your app is now ready to onboard user data into your application.

## Listen to Events

Impler instance provides `message` event listener which gets called for various events happening with the widget. Here is how to attach event listener,

```javascript
window.impler.on('message', (eventData) => {}, uuid);
```

`eventData` follows the `{ type, value}` structure.

<table><thead><tr><th width="241">type</th><th width="146">value</th><th>Description</th></tr></thead><tbody><tr><td><code>UPLOAD_STARTED</code></td><td>ImportData</td><td>User has started import by selecting file and clicking on <code>See Mapping</code></td></tr><tr><td><code>UPLOAD_TERMINATED</code></td><td>ImportData</td><td>The user canceled the import in the middle of the import process.</td></tr><tr><td><code>UPLOAD_COMPLETED</code></td><td>ImportData</td><td>The user has completed the import.</td></tr><tr><td><code>CLOSE_WIDGET</code></td><td></td><td></td></tr></tbody></table>

Have any questions? Feel free to ping us over [discord](https://discord.impler.io).
