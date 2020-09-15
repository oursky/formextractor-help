---
description: >-
  This step-by-step tutorial covers how Auto Extraction Items of FormX work on a
  wide range of documents
---

# Set up a form without master image

## Prerequisites

* An account on FormX [portal](https://formextractor.oursky.com/)
* Have basic understanding on [background](../background.md) of FormX
* Download [samples](https://drive.google.com/drive/folders/15ozbfqMwXjjDd9J-YfFZH2DbVB2euQz3?usp=sharing) that will be used in this tutorial

## Aims

Obtain { date, time, total amount } from receipts and invoices in Chinese and English.

## Create a Form

Navigate to the form listing page of FormX and click the "Add New Form" button on top right corner.

![](../.gitbook/assets/screenshot-2020-09-10-at-3.58.36-pm.png)

You will be promoted with a Create Form modal. Name this form "" and upload the `master_image.jpg` from the downloaded sample name cards. Then click "Create".

![](../.gitbook/assets/screenshot-2020-09-11-at-6.55.12-pm.png)

A new form with no master image will be created. 

![](../.gitbook/assets/screenshot-2020-09-11-at-6.57.33-pm.png)

## Set up the form

Go in the form and navigate to the "Settings" tab on the right bar， then change the "Document Type" to "Receipt". Once "Receipt" is picked, three Auto Extraction Items will be automatically ticked. Be sure to save before you proceed.

![](../.gitbook/assets/screenshot-2020-09-11-at-7.02.35-pm.png)

A bit of background knowledge first before we proceed. 

### Document Type

Some predefined document types are provided for user to choose from. Once selected, corresponding Auto Extraction Items will be automatically ticked, with some optional ones left unchanged like "Address" when the "Receipt" type is chosen.

### Auto Extraction Items

Independent from the master image, these items are scanned throughout the entire image when one is uploaded. As a result, in this tutorial although the samples \(receipts and invoices\) do not have a shared format hence no master image, our targets can still be extracted.

## Test out stage

Now we can start testing. There are five samples in the zip file you have downloaded at the start of this tutorial with different appearance:

* `receipt_eng_food.jpg` - numerous creases and blurry texts
* `receipt_eng_clothing.jpg` - lots of background noises \(i.e. those english alphabets from the keyboard\)
* `receipt_chinese_equipment.jpg` -  a hand holding the receipt with words in the background
* `receipt_chinese_food.jpg` - a clear receipt slightly twisted
* `invoice_eng_clothing` - shadows from the phone capturing it and a stamp

As mentioned in each sample's description they pose various challenges to target data extraction, still FormX is capable to locate and pull the data off them accurately thanks to our well-designed training stage.

To validate the above statement, switch to the "Test" tab and throw each of them samples in. You will see the targets - { total amount, date, time } are all properly extracted. Here's a GIF demonstrating such a flow:

![](../.gitbook/assets/ezgif-6-02937d624ff9.gif)

## Integrate with any app

Extractions can be triggered through APIs, meaning FormX can be integrated to any app as long as one has API calling ability. Navigate to the "API" tab, then copy both the form ID and your access token by clicking the buttons on the top right corner. 

We will then try calling the API with curl. Copy our curl example, replace the corresponding placeholders then press enter! With the correct payload given you will soon get the results. Simply translate this curl command to whatever language you app is built with, and you have got FormX integrated.

If you'd like to learn more about the APIs, we do have a complete doc down the "API" tab.

## Done!

Assuming you have completed the master image [tutorial](set-up-a-form-with-master-image.md), you are well equipped and can start exploring FormX's wide range of features! 

