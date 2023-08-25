---
description: >-
  If you are using a (currently) unsupported client framework, you can use our
  embedded script. This will show the Widget inside an iframe.
---

# 🪄 iFrame Embed

## Add Script

You copy this snippet to your code before the closing body tag.

{% code overflow="wrap" %}
```html
<script type="text/javascript" src="https://embed.impler.io/embed.umd.min.js" async></script>
```
{% endcode %}

It will add `impler` variable in `window`, so you can call its `init` and `show` method.

## Initialize Widget

Before the widget gets shown you have to call its `init` method according to the following snippet,

```javascript
window.impler.init(projectId, { accessToken });
```

### Parameters

<table><thead><tr><th>Parameter</th><th>Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>projectId</td><td>string</td><td>true</td><td>Id of the project created from API</td></tr><tr><td>accessToken</td><td>string</td><td>false</td><td>Provide security Token if APIs are secured with <code>ACCESS TOKEN</code></td></tr></tbody></table>

## Show Widget

After the initialization, you can call `show` method to open the widget according to the following snippet,

```javascript
window.impler.show({ templateId });
```

### Parameters

<table><thead><tr><th>Parameter</th><th>Type</th><th data-type="checkbox">Required?</th><th>Description</th></tr></thead><tbody><tr><td>templateId</td><td>string</td><td>true</td><td>id of the template we're trying to do import.</td></tr><tr><td>extra</td><td>string</td><td>false</td><td><code>String</code> or <code>Stringified JSON Object</code> to pass while sending imported data</td></tr><tr><td>authHeadervalue</td><td>string</td><td>false</td><td>Authentication value to authenticate webhook while sending imported data</td></tr><tr><td>primaryColor</td><td>string</td><td>false</td><td>HEX or RGB color value to change color of buttons</td></tr><tr><td>colorScheme</td><td>string</td><td>false</td><td><code>dark</code> or <code>light</code> value presenting color scheme of app</td></tr><tr><td>title</td><td>string</td><td>false</td><td>Override default title of Import widget</td></tr></tbody></table>

That's it, your app is now ready to onboard user data into your application.

## Listen to Events

Impler instance provides `message` event listener to listen various events happening with widget. Here is how to attach event listener,

```javascript
window.impler.on('message', { type: string, value: any });
```

`value` will be latest upload information available while calling the listener function.

### Event Types

<table><thead><tr><th width="280">Name</th><th>Description</th></tr></thead><tbody><tr><td><code>WIDGET_READY</code></td><td>Import Widget is ready to import spreadsheet</td></tr><tr><td><code>UPLOAD_STARTED</code></td><td>User has started importing spreadsheet</td></tr><tr><td><code>UPLOAD_TERMINATED</code></td><td>User has terminated importing spreadsheet</td></tr><tr><td><code>UPLOAD_COMPLETED</code></td><td>User has completed importing spreadsheet</td></tr><tr><td><code>CLOSE_WIDGET</code></td><td>Import widget is closed</td></tr></tbody></table>
