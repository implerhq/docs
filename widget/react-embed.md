---
description: >-
  Impler provides the @impler/react package to add an import widget in your
  application
---

# 🌐 React Embed

Let's do a quick review of how to use `@impler/react` in your application.

## Add Script

You copy this snippet to your code before the closing body tag.

{% code overflow="wrap" %}
```html
<script type="text/javascript" src="https://embed.impler.io/embed.umd.min.js" async></script>
```
{% endcode %}

It will add `impler` variable in `window`, so you can call its `init` and `show` method.

## Install the Package

Add `@impler/react` in your application by running the following command.

```bash
npm i @impler/react
# or
yarn add @impler/react
```

## Add Import Button

`@impler/react` provides headless `useImpler` hook that you can use to show import widget in your application.

```javascript
import { useImpler } from '@impler/react';

const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
});

<button disabled={!isImplerInitiated} onClick={showWidget}>
    Import
</button>
```

### Props

<table><thead><tr><th>Prop</th><th>Type</th><th data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>projectId</td><td>string</td><td>true</td><td>Id of the project created from API</td></tr><tr><td>templateId</td><td>string</td><td>false</td><td>Id or Code of the Template you want to Import</td></tr><tr><td>accessToken</td><td>string</td><td>false</td><td>Provide security Token if APIs are secured with <code>ACCESS TOKEN</code></td></tr><tr><td>authHeaderValue</td><td>string</td><td>false</td><td>Authentication value to authenticate webhook while sending imported data</td></tr><tr><td>extra</td><td>string / json</td><td>false</td><td><code>String</code> or <code>JSON Object</code> to pass while sending imported data</td></tr><tr><td>primaryColor</td><td>string</td><td>false</td><td>Color to change widget theme colors</td></tr><tr><td>onUploadStart</td><td>(value) => void</td><td>false</td><td>Function that get's called when user starts upload</td></tr><tr><td>onUploadTerminate</td><td>(value) => void</td><td>false</td><td>Function that get's called when user leaves spreadsheet import in between</td></tr><tr><td>onUploadComplete</td><td>(value) => void</td><td>false</td><td>Function that gets called when user completes the import</td></tr><tr><td>onWidgetClose</td><td>() => void</td><td>false</td><td>Function that gets called when widget is closed</td></tr></tbody></table>
