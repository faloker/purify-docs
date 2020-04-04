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

Go to the unit report page for which you uploaded a report:

![Since the report was uploaded without the specified template, we need to apply a new one ](../.gitbook/assets/screenshot-2020-04-04-at-11.44.34.png)

Click on the **Apply Template** button and you will see the template configurator:

![Nine steps only](../.gitbook/assets/screenshot-2020-04-04-at-11.50.58.png)

### Step 1

You will need to select an array with issues. **Why?**   
Sometimes ****security tool reports may contain some additional debug or configuration information that is completely pointless to you. Purify will extract all arrays from the document and show you an example of their elements, you will need to **select an array containing the scan results**.

![Gitleaks report have only one array inside](../.gitbook/assets/screenshot-2020-04-04-at-12.02.34.png)

![Pretty obvious...](../.gitbook/assets/screenshot-2020-04-04-at-12.04.40.png)

### **Step 2**

Choose the fields that will be treated as the title and subtitle, just decide which combination of fields will be more suitable for you.

{% hint style="info" %}
You can select as many fields as you want, without restrictions.
{% endhint %}

![offender and rule looks good for us](../.gitbook/assets/screenshot-2020-04-04-at-12.06.43.png)

### Step 3

Based on the fields you choose previously you need to create patterns to display them. You can use any combination of characters or stay simple:

![](../.gitbook/assets/screenshot-2020-04-04-at-12.13.50.png)

### Step 4

Now we need to decide what fields represent issue body

![](../.gitbook/assets/screenshot-2020-04-04-at-12.19.07.png)

### Step 5

Here you need to select the types of fields, just so that everything is displayed correctly.

![base64? &#x1F914; BurpSuite uses this format to encode results...](../.gitbook/assets/screenshot-2020-04-04-at-12.20.29.png)

### Step 6

Now we come to a serious matter. You need to select the fields that will be used to find the same findings at the template 

![We want to track only unique offenders](../.gitbook/assets/screenshot-2020-04-04-at-12.25.35.png)

### Step 7

The last important step is to select fields that will be merged if the issues look the same \(**Step 6**\). Merging occurs only for issues within the same template.

{% hint style="info" %}
This step is **optional** because sometimes tools generate only unique findings and there is no need in merging
{% endhint %}

![It makes sense to merge file fields if the offenders are equal](../.gitbook/assets/screenshot-2020-04-04-at-14.01.32.png)

### Step 8

Let's say you decided to give a try [gitleaks](https://github.com/zricethezav/gitleaks), after using [truffleHog](https://github.com/dxa4481/truffleHog) \(yet another tool for finding secrets\). Obviously, you want to see only what's new gitleaks can find. 

That's why you need to select fields for which values Purify will perform a lookup **on all issues inside the unit**. If all these fields exist in any issue, Purify will treat the new issue as duplicate and will not process it.

![If the issue is about the same secret in some file, we will ignore it](../.gitbook/assets/screenshot-2020-04-04-at-14.09.57.png)

### **Step 9**

![Give a name and add some tags](../.gitbook/assets/screenshot-2020-04-04-at-12.50.22.png)

### Final

As result of these actions we have 16 new issues

![We have 16 new findings and 12 were merged or previously seen in this unit](../.gitbook/assets/screenshot-2020-04-04-at-14.11.20.png)

Now go to the issues and explore them all

![Title and subtitle fields](../.gitbook/assets/screenshot-2020-04-04-at-14.43.22.png)

![Body fields](../.gitbook/assets/screenshot-2020-04-04-at-14.43.33.png)

If you are messed up with the template and want, for example, to change the way the title and subtitles are displayed, see this page.

