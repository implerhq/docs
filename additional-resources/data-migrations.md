---
icon: route
description: Learn how to update your database data through migrations.
---

# Data Migrations

Occasionally, Impler might add features that call for data or database schema alterations. This typically occurs when a feature requires certain data to be present on a database entity to function. To make these modifications to your database, you can utilize migrations.

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

Certain features can require more than one migration; in that case, you must do each migration in the following order.

## Migrations History

Below you will find a list of migrations introduced in previous versions of Impler, alongside the migration path to use in the script above.

<table><thead><tr><th width="126">Version</th><th width="235">Feature</th><th>Migration Path(s)</th></tr></thead><tbody><tr><td><a href="https://github.com/implerhq/impler.io/releases/tag/v0.16.0"><code>v0.16.0</code></a></td><td>Date format consideration</td><td><code>./src/update-date-formats/update-date-formats.migration.ts</code></td></tr><tr><td><a href="https://changelog.impler.io/february-2024/v0.17.0-select-sheet-modal-add-column-improvements-and-column-ordering-facility"><code>0.17.0</code></a></td><td>Revision of template files according to new structure</td><td><code>./src/migrations/regenerate-templates/regenerate-templates.migration.ts</code></td></tr><tr><td><code>0.24.0</code></td><td>Verify user email using verification code</td><td><code>./src/migrations/verify-user/verify-user.migration.ts</code></td></tr><tr><td><code>0.27.0</code></td><td>Migrate users for teams support</td><td><code>./src/migrations/shift-environment-key/shift-environment-key.migration.ts</code></td></tr></tbody></table>

Have any doubts? Shoot us a message directly on [Discord](https://discord.impler.io).
