---
description: Here you can a way how to upload your reports to Purify.
---

# Reports

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

## Uploading

### File

Now you can upload the report as **JSON** or **XML** file.

{% hint style="warning" %}
The parameter **unit** represents a **slug**, not a unit name. In the example below

```text
unit=gitleaks-test
```

It means that the project name is **gitleaks** and the unit name is **test**.
{% endhint %}

```bash
http -f POST https://purify-demo.herokuapp.com/api/upload/file/main-examples \
    "apikey: xxxxxxxxx"  \
    file@Downloads/zap-example.xml
```

If you already created a template for such tool, you need to provide it, so report content will be parsed automatically

```bash
http -f POST https://purify-demo.herokuapp.com/api/upload/file/main-examples/zap \
    "apikey: xxxxxxxxx"  \
    file@Downloads/zap-example.xml
```

### Oneshot

In addition, you can upload your results as separate JSON objects. The most common use case is getting events from the webhook from other tools or systems.

To upload a oneshot:

```bash
http POST https://purify-demo.herokuapp.com/api/upload/oneshot/main-examples \
    "apikey: xxxxxxxxx" \
    < Downloads/gitleaks-one-object.json
```

## API Reference

[https://purify-demo.herokuapp.com/swagger/\#/upload](https://purify-demo.herokuapp.com/swagger/#/upload)

