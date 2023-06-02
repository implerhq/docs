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
window.impler.init(projectId, { accessToken, template });
```

### Parameters

<table><thead><tr><th>Parameter</th><th>Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>projectId</td><td>string</td><td>true</td><td>Id of the project created from API</td></tr><tr><td>accessToken</td><td>string</td><td>false</td><td>Provide security Token if APIs are secured with <code>ACCESS TOKEN</code></td></tr><tr><td>template</td><td>string</td><td>false</td><td>Id or Code of the Template you want to Import. If not specified select template option will be shown to user during Import.</td></tr></tbody></table>

## Show Widget

After the initialization, you can call `show`  method to open the widget according to the following snippet,

```
window.impler.show({ extra, authHeaderValue });
```

### Parameters

<table><thead><tr><th>Parameter</th><th>Type</th><th data-type="checkbox">Required?</th><th>Description</th></tr></thead><tbody><tr><td>extra</td><td>string</td><td>false</td><td><code>String</code> or <code>Stringified JSON Object</code> to pass while sending imported data</td></tr><tr><td>authHeadervalue</td><td>string</td><td>false</td><td>Authentication value to authenticate webhook while sending imported data</td></tr></tbody></table>

That's it, your app is now ready to onboard user data into your application.
