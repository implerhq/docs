---
description: >-
  Default value facility empowers developers to specify fallback values for
  empty or missing columns. This ensures data consistency and completeness while
  receiving the data.
icon: swap
---

# Default Value

Till the date, if imported spreadsheet contains missing value or any column is not mapped, the response uses `{{key}}` as placeholder. By utilizing Default Value functionality developer has more control over format of response they will receive.

## Setting Default Values

Default value can be applied to columns either at the time of adding column or updating column. Wildcard values like `null`, `undefined` can also be used, which available in the dropdown.

Means developer can choose one of these predefined values or write default value as a string of their choice.

1. **null**: Represents the null value.
2. **undefined**: Represents an undefined value.
3. **Empty String**: Represents an empty string.
4. **Empty Array (\[])**: Represents an empty array.
5. **Boolean true**: Represents the boolean value `true`.
6. **Boolean false**: Represents the boolean value `false`.

While providing custom schema you can mention with `defaultValue` key and put your desired string or appropriate `value` from mentioned table.

| Label             | Value           |
| ----------------- | --------------- |
| null              | `<<null>>`      |
| undefined         | `<<undefined>>` |
| Empty String      | `<<>>`          |
| Empty Array (\[]) | `<<[]>>`        |
| Boolean true      | `<<true>>`      |
| Boolean false     | `<<false>>`     |

## When default value gets applied?

The provided default value is used when imported data gets sent to application as response. The default value will be applied to column when,

1. **Column Not Required and Not Selected During Mapping:**
   * When a column is not marked as required, and the user chooses not to select the column during the mapping phase, the default value will be used in response.
2. **Column Not Required and Contains Empty Value:**
   * When a column is not marked as required, and the column contains an empty value, the default value will be applied to fill the gap.

## Providing default value during [runtime-schema.md](runtime-schema.md "mention")

Web portal GUI makes it easy to assign default value to column.  Based on needs you can provide default value while providing schema during runtime too.

### Default Value example with [runtime-schema.md](runtime-schema.md "mention")

```javascript
// Custom Schema
const schema = {
  columns: [
    { name: "description", required: false, defaultValue: "<<undefined>>" },
    // Other columns...
  ],
};
```

The Default Value functionality provides flexibility and control to developers when importing data. Whether dealing with optional columns or handling empty values, this feature enhances the overall data import experience.

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
