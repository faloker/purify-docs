---
description: Purify + Slack
---

# \[DISABLED\] Slack

## Overview

There is one thing that Purify can do with Slack - send messages via webhook. That's it.

Currently, this awesome integration is used to notify you if:

* You got a report with new findings never seen before
* Jira ticket was resolved with status **Done** and Purify automatically resolved it

## Configuration

First, you will need a webhook from Slack, see [here](https://api.slack.com/messaging/webhooks) what you need to do.

Second, do the following:

```bash
http POST https://purifyhost/api/settings/slack \
    "apikey: your-api-key" \
    webhook="https://hooks.slack.com/services/xxxxxxx/xxxxxx/xxxxx"
```

 As a result you should see this:

![The name and logo can be changed in the settings of a Slack application](../.gitbook/assets/screenshot-2020-04-04-at-00.19.28.png)

## Examples

> You got a report with new findings never seen before

![](../.gitbook/assets/screenshot-2020-03-26-at-23.57.59.png)

> Jira ticket was resolved with status **Done** and Purify automatically resolved it

![](../.gitbook/assets/screenshot-2020-03-27-at-00.30.10.png)

