---
description: Learn how to update your database data through migrations.
---

# 🔄 Data Migrations

Occasionally, Impler might add features that call for alterations to the data or database schema. This typically occurs when a feature requires certain data to be present on a database entity to function. To make these modifications to your database, you can utilize migrations.

## Running Migrations

To run data migrations, enter the following sequence of commands in your terminal from the [`impler/api`](https://github.com/implerhq/impler.io) repository root:

{% code overflow="wrap" fullWidth="false" %}
```bash
npm run setup:project
cd apps/api
npm run migration -- ./src/migrations/<MIGRATION_PATH>.ts
# e.g. npm run migration --  ./src/migrations/update-date-formats/update-date-formats.migration.ts
```
{% endcode %}

Certain features can require more than one migration; in that case, you'll need to do each migration in the following order.

## Migrations History

Below you will find a list of migrations introduced in previous versions of Impler, alongside the migration path to use in the script above.

<table><thead><tr><th width="145">Version</th><th width="235">Feature</th><th>Migration Path(s)</th></tr></thead><tbody><tr><td><a href="https://github.com/implerhq/impler.io/releases/tag/v0.16.0"><code>v0.16.0</code></a></td><td>Date format consideration</td><td><code>./src/update-date-formats/update-date-formats.migration.ts</code></td></tr><tr><td><a href="https://changelog.impler.io/february-2024/v0.17.0-select-sheet-modal-add-column-improvements-and-column-ordering-facility"><code>0.17.0</code></a></td><td>Revision of template files according to new structure</td><td><code>./src/migrations/regenerate-templates/regenerate-templates.migration.ts</code></td></tr></tbody></table>

