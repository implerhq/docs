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

## Applying App's Color Scheme

Your application may be developed by keeping dark and light modes in mind. So to let the Import widget show the widget overlay properly, you need to pass `colorScheme` in `showWidget` function.

Allowed values for colorScheme are **light** or **dark**.

```javascript
showWidget({ colorScheme: 'light' })
```

## [Data Seeding](../platform/data-seeding.md) in Sample File

You can provide default data to fill in the Sample file that gets generated from the Import widget. Default data act as a placeholder for the user to further add or update the data.

Here is an example of how to provide data to fill in the sample file,

```javascript
showWidget({
  data: [
      { country: 'ABC' },
      { country: 'DEF' },
      { country: 'GHE' },
  ]
});
```

## Providing [Runtime Schema](../platform/runtime-schema.md)

The schema and output provided in the [web.impler.io](https://web.impler.io) portal for any import behave as default values for any Import. It's possible to override the default schema and output, to adapt dynamic nature of Import.

Here is an example of how to provide dynamic schema and output,

```javascript
showWidget({
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

## Passing Extra Parameters

It's an obvious need that we want to pass `userId` or `orgId` representing who imported the data. In that case, you can pass that data in an extra parameter.

You can pass `string`, `object`, or `array` in extra. Here is an example of how to do it,

```javascript
const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
    extra: {
        userId: '4ddhodw3',
        time: new Date().this string()
    }
});
```

The extra parameters get sent to an application during the webhook call.

## Changing Import Title

By default, the Import widget takes the name of the Import to show in the title. But it's possible to change the `title` from the implementation side too. Helpful to keep the title separate from what the name is given in the web portal.

Here is how,

```javascript
const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
    title: "Employee Import"
});
```

## Changing Theme Color

You can pass a primary color to the import widget, which will update the colors of all buttons accordingly to match your app's theme color.

```javascript
const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
    primaryColor: '#5f45ff'
});
```

## Providing Authentication Header Value

In case the backend endpoint is authenticated with the token, it's possible to provide token value from the implementation side. You can provide a **string** or **async function** that returns the token value.

```javascript
const { showWidget, isImplerInitiated } = useImpler({
    templateId: "",
    projectId: "",
    accessToken: ""
    authHeaderValue: async () => {
        return "..."
    }
});
```
