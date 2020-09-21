---
description: Welcome to the Purify documentation!
---

# Introduction

![](.gitbook/assets/blank-diagram-6-.png)

## Description

The goal of Purify to be an easy-in-use and efficient tool to simplify a workflow of managing vulnerabilities delivered from various \(even customs\) tools.

Purify is aims to be a tool-agnostic application. Tool independence makes it possible to analyze reports of **any tool**. Technically, the report you want to upload should be one of the following:

* JSON file
* XML file
* JSON object \(most webhooks dispatch events as separate JSON objects\)

This means **you don't need any special plug-ins** to parse incoming reports. For this Purify introduces the concept of templates. Templates are code-free and user-friendly structures that parse reports the way you tell them.

Purify is able to remove duplicate results among various vulnerability scanners or tools. In addition, it can combine several results of the same tool based on some fields and it is fully configurable. Purify does all this work to reduce the headache of the analyst.

Collect all your findings in one place, review/validate/track them, collaborate with your teammates, receive notifications via Slack, create Jira tickets and many more.

## About this document

This documentation is dedicated for somebody who are going to use Purify.

{% hint style="warning" %}
In the rest of the documentation, all HTTP requests in snippets are performed using [httpie](https://httpie.org/).
{% endhint %}

