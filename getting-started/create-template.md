---
description: >-
  How templates work. How to create a good template. Caveats and examples of
  template creation.
---

# Templates

## Overview

The purpose of templates is to parse incoming reports to extract findings, remove duplicates and merge findings which have something in common. That means that the way you create a template will define how you will operate with the findings of a particular tool.

## Requirements

You need to upload a report to Purify. See how to do it [here](upload-report.md). 

{% hint style="info" %}
If you do not have any reports at hand, you can use reports from [here](../report-samples.md).
{% endhint %}

## Action

In this section we will go through all steps of template creation.

Go to the reports page for which unit you uploaded a report:

![](../.gitbook/assets/screenshot-2020-10-25-at-17.57.41.png)

Click on the **Create Template** button and you will see the **Template Configurator**:

![](../.gitbook/assets/screenshot-2020-10-25-at-17.59.58.png)

### Step 1

You will need to select an array with issues. **Why?**

Sometimes ****security tools reports may contain some additional debug or configuration information that is completely pointless to you. Purify will extract all arrays from the document and show you an example of their elements, you will need to **select an array containing the scan results**.  


![Gitleaks has only one array inside, so it&apos;s pretty obvious](../.gitbook/assets/screenshot-2020-10-25-at-18.02.05.png)

### **Step 2**

Choose the fields that will be treated as the title and subtitle, just decide which combination of fields will be more suitable for you.

{% hint style="info" %}
You can select as many fields as you want, without restrictions.
{% endhint %}

![offender and rule looks good for us](../.gitbook/assets/screenshot-2020-04-04-at-12.06.43.png)

### Step 3

Sometimes findings delivered with severity field, you can select this field on the third step:

![Gitleaks do not provide severity field, so Purify will set it to Medium by default](../.gitbook/assets/screenshot-2020-10-25-at-18.03.15.png)

### Step 4

Based on the fields you choose previously you need to create patterns to display them. You can use any combination of characters or stay simple:

![](../.gitbook/assets/screenshot-2020-10-25-at-18.06.39.png)

### Step 5

Now we need to decide what fields will represent issue body:

![](../.gitbook/assets/screenshot-2020-10-25-at-18.07.09.png)

### Step 6

Here you need to select the field types so that everything is displayed correctly. Optionally, you can change the display names for the fields if the default is not meaningful enough:

![](../.gitbook/assets/screenshot-2020-10-25-at-18.07.49.png)

### Step 7

Now we come to a serious matter. You need to select the fields that will be used to find the same findings at the template 

![We want to track only unique offenders](../.gitbook/assets/screenshot-2020-10-25-at-18.09.39.png)

### Step 8

The last important step is to select fields that will be merged if the issues look the same \(**Step 7**\). Merging occurs only for issues within the same template.

{% hint style="info" %}
This step is **optional** because sometimes tools generate only unique findings and there is no need in merging
{% endhint %}

![It makes sense to merge file and commit fields if the offenders are the same](../.gitbook/assets/screenshot-2020-10-25-at-18.10.12.png)

### Step 9

Let's say you decided to give a try [gitleaks](https://github.com/zricethezav/gitleaks), after using [truffleHog](https://github.com/dxa4481/truffleHog) \(yet another tool for finding secrets\). Obviously, you want to see only what's new gitleaks can find. 

That's why you need to select fields for which values Purify will perform a lookup **on all issues inside the unit**. If all these fields exist in any issue, Purify will treat the new issue as duplicate and will not process it.

![If the issue is about the same secret in some file, we will ignore it](../.gitbook/assets/screenshot-2020-10-25-at-18.11.24.png)

### **Step 10**

![Give a name and add some tags](../.gitbook/assets/screenshot-2020-10-25-at-18.12.19.png)

### Final

As result of these actions we have 16 new issues

![We have 17 new findings and 11 were merged or previously seen in this unit](../.gitbook/assets/screenshot-2020-10-25-at-18.13.20.png)

Now go to the **Issues** tab and explore them all:

![](../.gitbook/assets/screenshot-2020-10-25-at-18.14.34.png)

![](../.gitbook/assets/screenshot-2020-10-25-at-18.15.48.png)

