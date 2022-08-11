# Tests available

## Bash Automated Testing System 

### test.bats

General tests for Hestia currently ran each PR a special config file is create each time test.bats runs. 

It currently covers a lot of the most used command. How ever it is not fully done.

### restore.bats

Preforms restore tests currently:

- HestiaCP GZIP
- HestiaCP ZSTD
- VestaCP GZIP

Available from https://hestiacp.com/testing/data/

### letsencrypt.bats 

Preforms testing of Let's Encrypt against the staging server for Let's Encrypt requires a special config to be present on the test server:

Requieres a special config file ()/tmp/hestia-le-env.sh)
```
#!/bin/bash 

user="user"
domain="domain.com"
ip="x.x.x.x"
```

Please note that domain.com needs to be a working domain and can't have Cloudflare proxy enabled!

### api.bats

Preforms tests regarding DNS cluster and a few "general" commands over the api. To run the test a remote server is requierd. 

Requieres a special config file (/tmp/hestia-api-env.sh)

```
#!/bin/bash 

server="hostname.com"
port="8083"
password="adminpassword"
# run v-generate-api-key
apikey="apikey" 
# Access key with sync-dns-cluster permissions
accesskey="access:secretkey"
```

### checks.bats

Is used to test the validation function in /func/main.sh

### wildcard.bats

Similar as letsencrypt.bats but uses a wildcard certificate to run the tests. As this test requires a locally hosted DNS server for this feature we currently don't run the test always

Requieres a special config file (/tmp/wildcard.sh)
```
#!/bin/bash 

# User need to exists with a valid domain name added as DNS domain will be used to request SSL against Letsencrypt Staging api
domain="domain.com"
user="user"
ip="1.x.x.x"
```

## Other methods

### Shell check

Run shellcheck on a docker current koalaman/shellcheck-alpine:v0.8.0 due to an issue with the lastest 

### PHP check

Linting via php8.1 it is currently limted to only the basic linting..
