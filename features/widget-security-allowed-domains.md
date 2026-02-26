---
description: >-
  Restrict which browser-based requests can use your API key and widget by
  whitelisting specific domains.
icon: shield-check
---

# Widget Security (Allowed Domains)

By default, your Impler API key can be used from any origin. When your API key is embedded in a frontend app, it's visible to anyone who inspects the page source — meaning someone could copy it and embed your Impler widget on their own site. **Allowed Domains** prevents this by telling Impler which browser origins are permitted to use the key.

> **Important:** This restriction applies only to browser-originated requests where an `Origin` or `Referer` header is present. Server-to-server API calls (e.g. from your backend, CI pipelines, or scripts) do not send these headers and are **not affected** by this setting, regardless of what domains are configured.

## How It Works?

When an allowed domains list is configured, Impler inspects the <mark style="color:$danger;">`Origin`</mark> (or <mark style="color:$danger;">`Referer`</mark>) header on each incoming request:

* If the header is **absent** (typical of server-to-server calls) → request proceeds normally
* If the header is **present and matches** an allowed domain → request proceeds normally
* If the header is **present but not on the list** → request is rejected with <mark style="color:$danger;">`401 Unauthorized`</mark>

If no domains are configured at all, all origins are permitted — this is the default, so existing integrations are unaffected.

***

## Who Can Manage Allowed Domains?

> #### 🔐 Only the project creator can update the allowed domains list.

Impler enforces this at the API level. When saving allowed domains, the system validates that the authenticated user is the **same user who originally created the project**. Team members who were invited to the project cannot modify this setting, even if they have other access.

This ensures that a sensitive security configuration like domain restrictions can only be changed by the person who owns the project — preventing collaborators from accidentally or maliciously unlocking access to untrusted origins.

If you are a team member and need to update this setting, contact the project owner.

***

## Configuring Allowed Domains

1. Go to your project's **Settings** page in the Impler web app.
2. Click the **Widget Security** tab.
3. In the **Allowed Domains** input, type a domain (e.g. <mark style="color:$danger;">`https://yourapp.com`</mark>) and press **Enter** to add it.
4. Add as many domains as needed.
5. Click **Save Domains**.

> **Note:** Only <mark style="color:$danger;">`http://`</mark> and <mark style="color:$danger;">`https://`</mark> origins are accepted. Domains are matched on <mark style="color:$danger;">`protocol + host`</mark> — so <mark style="color:$danger;">`https://yourapp.com`</mark> and <mark style="color:$danger;">`https://yourapp.com/`</mark> are treated as the same entry, but <mark style="color:$danger;">`http://yourapp.com`</mark> and <mark style="color:$danger;">`https://yourapp.com`</mark> are treated as different origins.

***

## Example

Say your widget is embedded on <mark style="color:$danger;">`https://app.yourcompany.com`</mark>. Configure it like this:

```
https://app.yourcompany.com
```

Now any API request made with your project's API key from <mark style="color:$danger;">`https://malicious-site.com`</mark> will be rejected automatically, while your widget continues to work normally.

If you have multiple environments or domains, add all of them:

```
https://app.yourcompany.com
https://staging.yourcompany.com
http://localhost:3000
```

***

## Behavior Reference

<table><thead><tr><th>Scenario</th><th>HTTP Status</th><th>Result</th></tr></thead><tbody><tr><td>No allowed domains configured</td><td><pre><code>200
</code></pre></td><td>All origins permitted</td></tr><tr><td>Request has no <mark style="color:$danger;"><code>Origin</code></mark>/<mark style="color:$danger;"><code>Referer</code></mark> header (server-to-server)</td><td><pre><code>200
</code></pre></td><td>Always allowed, restriction does not apply</td></tr><tr><td>Origin matches an allowed domain</td><td><pre><code>200
</code></pre></td><td>Request allowed</td></tr><tr><td>Origin does NOT match any allowed domain</td><td><pre><code>401 Unauthorized
</code></pre></td><td><pre><code>Domain not allowed
</code></pre></td></tr><tr><td>Non-creator tries to update allowed domains</td><td><pre><code>404 Not Found
</code></pre></td><td><pre><code>Project not found
</code></pre></td></tr><tr><td>Project creator updates allowed domains</td><td><pre><code>200
</code></pre></td><td>Allowed ✅</td></tr></tbody></table>

***

## Clearing All Allowed Domains

To go back to allowing all origins, remove all entries from the **Allowed Domains** input and click **Save Domains**. An empty list disables the restriction.

***

## Frequently Asked Questions

<details>

<summary><strong>Does this affect server-to-server API calls?</strong></summary>

No. The restriction only applies to requests that carry an <mark style="color:$danger;">`Origin`</mark> or <mark style="color:$danger;">`Referer`</mark> header, which browsers automatically attach. Calls from your server, scripts, or tools like Postman do not include these headers and are never blocked.

</details>

<details>

<summary><strong>Can I add </strong><mark style="color:$danger;"><strong><code>localhost</code></strong></mark><strong> for local development?</strong></summary>

Yes. Add <mark style="color:$danger;">`http://localhost:3000`</mark> (or whichever port you use) as an allowed domain during development and remove it before going to production.

</details>

<details>

<summary><strong>What happens if I misconfigure and lock myself out?</strong></summary>

You can always update the allowed domains list from the Impler dashboard — the settings UI is authenticated via your user session, not the API key, so it remains accessible regardless.

</details>

<details>

<summary><strong>I'm a team member but I can't change the Widget Security settings. Why?</strong></summary>

This setting is restricted to the project creator only. Reach out to the person who originally created the project to make changes.

</details>

