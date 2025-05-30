---
description: >-
  Customise your import widget to match your brand and design system using the
  AppearanceConfig options.
icon: text-size
---

# Widget Customization

## Basic Example and Setup

```javascript
const { showWidget, isImplerInitiated } = useImpler({
  projectId: "673b4749998f0403d8491f59",
  templateId: "6839498aec2bd4236c74ebda",
  accessToken: "dde9212958056095b59ebe39a897d369",
  appearance: {
    primaryColor: '#FF6B35',
    fontFamily: 'Inter',
    borderRadius: '8px'
  }
});
```



## **AppearanceConfig type definition**    &#x20;

```typescript
export type AppearanceConfig = {
  widget?: {
    backgroundColor?: string;
  };
  primaryColor?: string;
  fontFamily?: string;
  borderRadius?: string;
  primaryButtonConfig?: ButtonConfig;
  secondaryButtonConfig?: ButtonConfig;
};
```

```typescript
export type ButtonConfig = {
  backgroundColor?: string;
  buttonShadow?: string;
  textColor?: string;
  hoverBackground?: string;
  hoverBorderColor?: string;
  borderColor?: string;
  hoverTextColor?: string;
};

```

Note - All properties, including the `appearance` object, are optional. If none are provided, the widget will fall back to its default appearance.



## ApperaranceConfig Property with Available Customization Options

**Widget Properties:**

* `backgroundColor` - Sets the main widget background color
* `primaryColor` - Main brand color used throughout the widget
* `fontFamily` - Font family for all text elements
* `borderRadius` - Corner rounding for all elements

**Button Properties:**

* `backgroundColor` - Button background color (default state)
* `textColor` - Button text color (default state)
* `borderColor` - Button border color (default state)
* `buttonShadow` - Drop shadow effect
* `hoverBackground` - Background color when hovering
* `hoverTextColor` - Text color when hovering
* `hoverBorderColor` - Border color when hovering



### Quick Note

⚠️ **Important:** We're moving `primaryColor` inside the `appearance` object. The old way still works but will be deprecated in future releases.

{% include ".gitbook/includes/your-feedback-is-crucial-in....md" %}
