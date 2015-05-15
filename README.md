# New Relic considerations for 18F

## ssl
You must enable ssl.
```
ssl = true
```

## Transaction Tracer
Don't change to `raw`, if you need to capture specific values use something other than New Relic.
```
transaction_tracer.record_sql = obfuscated
```

# Browser Monitoring
Weigh the security implications of dynamically inserting javascript into the browser.


Right now, there is one example file for a fisma-low python project. It would be great to expand that to include ruby and node examples as well as other considerations for higher risk projects.