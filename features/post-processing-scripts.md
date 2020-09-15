---
description: >-
  Allowing users to write their own post processes in JavaScript, outputs from
  Detection Regions become customizable.
---

# Post-processing Scripts

## A quick guide

At times a user may want to process the output from Detection Regions as OCR services can return some false or not so perfect results, such as some incorrectly recognized characters or extra whitespaces. With post-processing scripts, they can apply filters to strip unwanted characters and add mappings to correct indesirable results.   
Another possible case is that the user wish to reformat or restructure the returned results. By adding custom JS script, one can twist the returned data to whatever s/he desires.

## How to add your own Script

In a Form's editor, create a Detection Region. The active tab in the right bar will automatically be switched to "Labeller", change "Type" to "Script":

![](../.gitbook/assets/screenshot-2020-09-15-at-7.31.27-pm%20%281%29.png)

Then press "Edit Script" to open up the script editor where you can input your own in JavaScript:

![](../.gitbook/assets/screenshot-2020-09-15-at-7.16.32-pm.png)

In fact, we have used this feature ourselves quite frequently. Almost all [templates](templates.md) have a few Detection Regions' type marked as "Script" where various text processing functions are applied.

