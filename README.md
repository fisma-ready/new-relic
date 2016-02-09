# New Relic considerations

Considerations for using New Relic in the federal government.

Below is a description of the settings in your New Relic `.ini` file that concern privacy and security. Example configuration files can be found in this repository:

* [`python-low-security.ini`](python-low-security.ini)

### An encrypted TLS connection

Enable TLS to encrypt and authenticate connections between your server and the New Relic servers.

```
ssl = true
```

The setting is called `ssl` after the old, now-deprecated SSL protocol. New Relic [has disabled SSLv3](https://discuss.newrelic.com/t/server-monitoring-is-giving-ssl-error/14704).

### Transaction Tracer

Leave the transaction SQL tracer to `obfuscated`.

```
transaction_tracer.record_sql = obfuscated
```

Don't change to `raw`. If there are specific, potentially user-provided or user-stored values you need to capture, use something other than New Relic to do it, such as your own local database.

### Browser Monitoring

New Relic has a setting to auto-insert a `<script>` tag that includes a JavaScript file, hosted by New Relic, into templates for some Python app frameworks.

By default, we recommend leaving the in-browser monitoring snippet off.

```
browser_monitoring.auto_instrument = false
```

Before enabling this, weigh the privacy and security implications of dynamically inserting third-party JavaScript into the browser.

All JavaScript references to third-parties silently share visitor browsing information with those third parties. Additionally, dynamically executing third-party JavaScript introduces an additional vector for attacking the security of your visitors.

### TODO

Right now, there is one example file for a low-risk Python project. It would be great to expand that to include Ruby and Node examples as well as other considerations for higher risk projects.