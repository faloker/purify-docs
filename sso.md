---
description: Here you can find instructions on how to configure authentication via SAML.
---

# SSO

## Overview

Purify can be configured to use SSO \(based on SAML\) instead of local authentication.

Under the hood [passport-saml](https://github.com/bergie/passport-saml) is used to make it possible.

## Configuration

You need to provide a set of credentials via `.env` file:

```bash
SAML_CALLBACK_URL=https://<server_fqdn>/api/auth/saml/callback
SAML_IDP_URL=https://dev-xxxx-xxx.us.auth0.com/xxx/xxxxx
SAML_ENTITY_ID=urn:dev-xxxx-xxx.us.auth0.com


SAML_LOCAL_KEY_PATH=/etc/certs/key.pem
# or
#SAML_LOCAL_KEY_ONELINE=MIIJQwIBADANBgkqhkiG9....

SAML_IDP_CERT_PATH=/etc/certs/idp.pem
# or
#SAML_IDP_CERT_ONELINE=MIIDDTCCAfWgAwIBAgIJcr....

SAML_EMAIL_FIELD_NAME=email
SAML_USERNAME_FIELD_NAME=name
```

`SAML_LOCAL_KEY_PATH` or `SAML_LOCAL_KEY_ONELINE` can be set in two ways: 

* via path of the mounted file into the docker container
* alternatively a single line private key without start/end lines where all rows are joined into single line, see example from of [singleline private key](https://github.com/bergie/passport-saml/blob/master/test/static/singleline_acme_tools_com.key).

The same work for `SAML_IDP_CERT_PATH` and `SAML_IDP_CERT_ONELINE`.

And set:

```bash
USE_SAML=true
```

## Action

Restart Purify and try to login. Connection errors will appear in logs.

The new button will appear on the `/welcome` screen:

![](.gitbook/assets/screenshot-2020-06-24-at-23.16.09.png)

## Extra

After enabling SSO, it might make sense to remove the registration flow.

To do so, set `ALLOW_REGISTRATION=false` in your `.env` file.

