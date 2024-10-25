---
icon: angular
description: >-
  Using @impler/angular package you can embed CSV Excel Importer into your
  application with just few lines of code.
---

# Angular Embed

Here is the step-by-step guide to embed CSV Excel Importer into your angular application using `@impler/angular`.

### Add Script

You copy this snippet to your code before the closing body tag.

{% code overflow="wrap" %}
```html
<script type="text/javascript" src="https://embed.impler.io/embed.umd.min.js" async></script>
```
{% endcode %}

It will add `impler` variable in `window`, so you can call its `init` and `show` method.

### Install the Package

Add `@impler/angular` in your application by running the following command.

```bash
npm i @impler/angular
# or
yarn add @impler/angular
```

### Use Impler Service

`@impler/angular` provides `ImplerService` that you can use to initialize and show an importer to your application.

```typescript
import { RouterOutlet } from '@angular/router';
import { isPlatformBrowser } from '@angular/common';
import { Component, Inject, PLATFORM_ID } from '@angular/core';
import { EventCalls, EventTypesEnum, ImplerService } from '@impler/angular';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [RouterOutlet],
  templateUrl: './app.component.html',
  styleUrl: './app.component.css',
})
export class AppComponent {
  title = 'impler-app';

  constructor(
    private implerService: ImplerService,
    @Inject(PLATFORM_ID) private platformId: Object
  ) {
    if (isPlatformBrowser(platformId)) {
      this.implerService.initializeImpler();
    }
  }
  public show(): void {
    this.implerService.showWidget({
      colorScheme: 'dark',
      projectId: '...',
      templateId: '...',
      accessToken: '...',
    });
  }
}
```

### Customize Texts

You can customize any text in the import widget, here is the sample. All customizable texts are available at [#available-texts](text-customization.md#available-texts "mention").

```typescript
public show(): void {
  this.implerService.showWidget({
    ...
    texts: {
      STEPPER_TITLES: {
        REVIEW_DATA: 'Check Data', // New Title
      },
    }
  });
}
```

### Listening for Events

<table><thead><tr><th>Event Name</th><th width="145">Data Type</th><th>Description</th></tr></thead><tbody><tr><td>UPLOAD_STARTED</td><td>Upload Partial Information</td><td>An event that gets triggered when a user starts the upload.</td></tr><tr><td>UPLOAD_TERMINATED</td><td>Upload Partial Information</td><td>An event that gets triggered when a user leaves import in the middle.</td></tr><tr><td>UPLOAD_COMPLETED</td><td>Upload Information</td><td>An event that gets triggered when a user completes the import.</td></tr><tr><td>CLOSE_WIDGET</td><td>-</td><td>An event that gets triggered when the widget is closed by the user.</td></tr><tr><td>DATA_IMPORTED</td><td>Imported Data</td><td>An event that gets triggered with all imported data. Read more at <a data-mention href="../data-retrieval/using-frontend-callback.md">using-frontend-callback.md</a></td></tr><tr><td>WIDGET_READY</td><td>-</td><td>An event that gets triggered when the import widget is opened.</td></tr></tbody></table>

#### Usage Example

```typescript
...
import { EventCalls, EventTypesEnum, ImplerService } from '@impler/angular';

@Component({
  ...
})
export class AppComponent {
  title = 'impler-app';

  constructor(
    private implerService: ImplerService,
    @Inject(PLATFORM_ID) private platformId: Object
  ) {
    if (isPlatformBrowser(platformId)) {
      this.implerService.initializeImpler();
      this.implerService.subscribeToWidgetEvents((eventData: EventCalls) => {
        switch (eventData.type) {
          case EventTypesEnum.DATA_IMPORTED:
            console.log('Data Imported', eventData.value);
            break;
          default:
            console.log(eventData);
            break;
        }
      });
    }
  }
}
```

### Applying App's Color Scheme

Your application may be developed by keeping dark and light modes in mind. So to let the Import widget show the widget overlay properly, you need to pass `colorScheme` in `showWidget` function.

Allowed values for colorScheme are **light** or **dark**.

```typescript
public show(): void {
  this.implerService.showWidget({
    ...
    colorScheme: 'dark',
  });
}
```

### [Data Seeding](../features/data-seeding.md) in Sample File

You can provide default data to fill in the Sample file that gets generated from the Import widget. Default data acts as a placeholder for the user to add or update the data further.

Here is an example of how to provide data to fill in the sample file,

```typescript
public show(): void {
    this.implerService.showWidget({
      data: [
          { country: 'Canada' },
          { country: 'Australia' },
          { country: 'Germany' },
      ]
    });
}
```

### Providing [Runtime Schema](../features/runtime-schema.md)

The schema and output provided in the [web.impler.io](https://web.impler.io) portal for any import behave as default values for any Import. It's possible to override the default schema and output, to adapt a dynamic nature of Import.

Here is an example of how to provide dynamic schema and output,

```typescript
public show(): void {
  this.implerService.showWidget({
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
}
```

### Advanced Validations <a href="#advanced-validations" id="advanced-validations"></a>

You can provide [#advanced-validations](angular-embed.md#advanced-validations "mention") in the column as `validations` key,

```typescript
public show(): void {
  this.implerService.showWidget({
    schema: [
      {
        "key": "Department Code",
        "name": "Department Code",
        "type": "String",
        "validations": [
          {
            "validate": "unique_with",
            "uniqueKey": "Employee No"
          }
        ]
      },
      {
        "key": "Employee Id",
        "name": "Employee Id",
        "type": "Number",
        "validations": [
          {
            "validate": "unique_with",
            "uniqueKey": "Employee No"
          }
        ]
      }
    ]
  });
}
```

### Using Typescript

If you're using typescript, you can leverage typescript types, like,

```typescript
import { useImpler, ColumnTypes, ValidationTypes } from '@impler/angular';

public show(): void {
  this.implerService.showWidget({
    schema: [
        {
          key: 'country',
          name: 'Country',
          type: ColumnTypes.STRING,
          "validations": [
            {
              "validate": ValidationTypes.LENGTH,
              "min": 5,
              "max": 100,
              "errorMessage": "Country Name must be between 5 to 100 characters"
            }
          ]
        }
    ]
  });
}
```

### Passing Extra Parameters

It's an obvious need that we want to pass parameters like `userId` or `orgId` representing who imported the data. In that case, you can pass that data in an extra parameter.

You can pass `string`, `object`, or `array` in extra. Here is an example of how to do it,

```typescript
public show(): void {
  this.implerService.showWidget({
    extra: {
      userId: '4ddhodw3',
      time: new Date().this string()
    }
  });
}
```

The extra parameters get sent to an application during the webhook call.

### Programmatically Closing Import Widget

Impler's import widget provides `closeWidget` a method that closes the import widget. Useful to close the import widget once data is imported.

```typescript
public close(): void {
    this.implerService.closeWidget();
}
```

### Changing Import Title

By default, the Import widget takes the name of the Import to show in the title. But it's possible to change the `title` from the implementation side too. Helpful to keep the title separate from what the name is given in the web portal.

```typescript
public show(): void {
    this.implerService.showWidget({
        title: "Employee Import"
    });
}
```

### Changing Theme Color

You can pass a primary color to the import widget, which will update the colors of all buttons accordingly to match your app's theme color.

```typescript
public show(): void {
    this.implerService.showWidget({
        primaryColor: '#5f45ff'
    });
}
```

### Providing Authentication Header Value

In case the backend endpoint is authenticated with the token, it's possible to provide token value from the implementation side. You can provide a **string** or **async function** that returns the token value.

```typescript
public show(): void {
    this.implerService.showWidget({
        authHeaderValue: async () => {
            return "..."
        }
    });
}
```

{% include "../.gitbook/includes/your-feedback-is-crucial-in....md" %}
