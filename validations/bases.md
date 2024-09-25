---
description: >-
  Utilize default validation options to build your desired data import
  experience.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🔰 Validators

## List of available validators:

1. **String Validator**: This validator ensures that the column value is a string. String and Number are both valid values.
2. **Number Validator**: The Number validator verifies that the column value is a valid numeric entry. It only permits numerical values like `12` but will not allow `12.33` and `john`.
3. **Double Validator**: The Double validator verifies that the column value is either a Number or a Number with decimals. Valid values are `12` and `12.5` but `john` is not valid.
4. **Email Validator**: With the Email validator, you can ensure that the column value conforms to a valid email format. Valid values look like `john@gmail.com` while values like `john` and `john.com` are not valid.
5. **Regex Validator**: The Regex validator enables you to define a custom regular expression pattern that the column value must match.
6. **Select Validator**: Use the Select validator to restrict column values to a predefined set of options. For instance, you can use it to ensure that a "Gender" column contains only values like "Male" or "Female."
7. **Any Validator**: Any validator offers maximum flexibility by allowing any value in the column.

### Validator Enhancements

* **isRequired**: Ensures that a value must exist in each cell for the column.
* **isUnique**: Ensures that the value is unique throughout the column.
* **allowMultiSelect**: Accepts multiple values separated by `,` for the cell.

It's possible to extend validation functionality to adjust according to your needs. Read more in [custom-validation.md](../features/custom-validation.md "mention").

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
