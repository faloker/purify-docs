---
description: Here you can a way how to upload your reports to Purify.
---

# Upload Report

## Requirements

To upload a report you need to have:

1. Project
2. Unit inside that project

Also, to work with API you need a token, to obtain it:

```bash
http POST https://purifyhost/api/auth/token \
    username="user" \
    password="pass"
```

## Action

Now you can upload a report

{% hint style="info" %}
The parameter **unit** represents a **slug**, not a unit name. It the example below

```text
unit=gitleaks-test
```

It means that the project name is **gitleaks** and the unit name is **test**.
{% endhint %}

```bash
http -f POST https://purifyhost/api/reports \
    "apikey: token" \
    "unit=gitleaks-test" \
    file@/path/to/gitleaks-report.json
```

If you already created a template for such tool, you need to provide it, so report content will be parsed automatically

```bash
http -f POST https://purifyhost/api/reports \
    "apikey: token" \
    "unit=gitleaks-test" \
    "template=gitleaks" \
    file@/path/to/gitleaks-report.json
```

