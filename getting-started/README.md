# Getting Started

## Architecture

Breakdown of the main parts of Purify.

### **Project**

The root component, can be a dedicated software project or a roaster of team projects.

### Unit

The direct child of a project, may represent releases, sub-projects, or any other type of separation that makes sense to you.

### Report

Belong to the unit. Delivered from any tool of your choice. The only requirement that it should be JSON or XML document.

{% hint style="success" %}
[How to upload a report](upload-report.md)
{% endhint %}

### **Template**

Using templates, you can remove duplicate results from the same tool, as well as similar findings from different tools.

{% hint style="success" %}
[How to create a template](create-template.md)
{% endhint %}

### Issue

Extracted from the report and formatted based on the template. The Issue is a flexible representation of the results from the report, because you decide which field to display and how.

{% hint style="success" %}
[How to operate with issues](issues.md)
{% endhint %}

## Play with it

There is a [demo instance of Purify](https://purify-demo.herokuapp.com), feel free to play with it. This instance contains enough data to take a look at all the basic functions of Purify.

You can find reports samples [here](../report-samples.md).





