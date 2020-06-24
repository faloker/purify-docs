---
description: Here you can find instructions on how to configure authentication via LDAP.
---

# LDAP

## Overview

Purify can be configured to support authentication through LDAP instead of local authentication. If you will enable LDAP authentication you will not be able to login with local user account.

Under the hood [passport-ldapauth](https://github.com/vesse/passport-ldapauth) is used to make it possible.

## Configuration

You need to provide a set of credentials via `.env` file:

```bash
LDAP_URL=ldaps://my.corp.net:636
LDAP_BIND_DN=admin
LDAP_BIND_CREDENTIALS=password
LDAP_SEARCH_BASE="dc=corp,dc=net"
LDAP_SEARCH_FILTER="(uid={{username}})"
```

And set:

```bash
USE_LDAP=true
```

{% hint style="info" %}
Purify will be able to communicate with your server through ldaps and you have no need to provide your internal certificate. It is possible due to the set option``tlsOptions: { rejectUnauthorized: false }`)``
{% endhint %}

## Action

Restart Purify and try to login. Connection errors will appear in logs.

Tweak `LDAP_SEARCH_FILTER` to include groups user should be part of.

## Extra

After enabling authentication via LDAP, it might make sense to remove the registration flow.

To do so, set `ALLOW_REGISTRATION=false` in your env file.

