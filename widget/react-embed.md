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

`@impler/react` provides headless `useImpler` hook that you can use to show an import widget in your application.

```jsx
import { useImpler } from '@impler/react';

const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
});

<button disabled={!isImplerInitiated} onClick={showWidget}>
    Import
</button>
```

{% hint style="info" %}
`isImplerIntiated` becomes _true_ when the import widget is ready to be open and importing data. It remains _false_ when there are some errors with the provided values. Errors get logged in the console panel of the browser.
{% endhint %}

### Props

<table><thead><tr><th>Prop</th><th width="145">Type</th><th width="147" data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>projectId</td><td>string</td><td>true</td><td>Id of the project</td></tr><tr><td>templateId</td><td>string</td><td>true</td><td>Id of the template</td></tr><tr><td>accessToken</td><td>string</td><td>true</td><td>Security token of project (available in <code>Settings</code> panel)</td></tr><tr><td>title</td><td>string</td><td>false</td><td>Import widget title, default will be Import Title</td></tr><tr><td>authHeaderValue</td><td>string</td><td>false</td><td>Authentication value to authenticate webhook while sending imported data</td></tr><tr><td>extra</td><td>string / json</td><td>false</td><td><code>String</code> or <code>JSON Object</code> to pass while sending imported data</td></tr><tr><td>primaryColor</td><td>string</td><td>false</td><td>Color to change widget theme colors</td></tr></tbody></table>

## Listening for Events

<table><thead><tr><th>Prop</th><th width="145">Type</th><th>Description</th></tr></thead><tbody><tr><td>onUploadStart</td><td>(value) => void</td><td>Function that get's called when user starts upload</td></tr><tr><td>onUploadTerminate</td><td>(value) => void</td><td>Function that get's called when user leaves spreadsheet import in between</td></tr><tr><td>onUploadComplete</td><td>(value) => void</td><td>Function that gets called when user completes the import</td></tr><tr><td>onWidgetClose</td><td>() => void</td><td>Function that gets called when widget is closed</td></tr></tbody></table>

#### Usage Example

```jsx
const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
    onUploadStart: (uploadInfo) => {
        console.log("User Started Importing", uploadInfo);
    },
    onUploadTerminate: (uploadInfo) => {
        console.log("User left Import in middle", uploadInfo);
    },
    onUploadComplete: (uploadInfo) => {
        console.log("User completed import", uploadInfo);
    },
    onWidgetClose: () => {
        console.log("Import widget is closed");
    }
});
```

## Handling Color Scheme

Your application may be developed by keeping dark and light modes in mind. So to let the Import widget show the widget overlay properly, you need to pass `colorScheme` in `showWidget` function.

Allowed values for colorScheme are **light** or **dark**.

```javascript
function onShowClick = () => {
    showWidget({ colorScheme: 'light' })
}
```

## [data-seeding.md](../platform/data-seeding.md "mention")

## [runtime-schema.md](../platform/runtime-schema.md "mention")
