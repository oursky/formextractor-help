---
description: >-
  This step-by-step tutorial will demonstrate how FormX can take care of the
  data extraction process from documents that share a format
---

# Set up a form with a master image

## Prerequisites

* An account on FormX [portal](https://formextractor.oursky.com)
* An understanding on [background](../background.md) of FormX's basics
* Sample [Business Registration (BR) Forms](https://drive.google.com/drive/folders/12hSnSbN2JyY\_iwi3XAhBiMxpp1wCvHib?usp=sharing) that will be used in this tutorial

## Objective

Obtain the following information from the business registration forms: {name of business}, {branch name}, {expiry date}.

## Creating a Form

Navigate to the form listing page of FormX and click the "Add New Form" button on the top right corner.

![](<../.gitbook/assets/Screenshot 2021-01-05 at 6.40.54 PM.png>)

You will be prompted with a Create Form modal. Name this form "business registration form" and upload the [`br_master_image.jpg`](https://drive.google.com/file/d/1YF3RddeqKW4J11vO9QhuiCOfWca9--Rh/view?usp=sharing) from the downloaded sample BR forms. Then click "Create":

![](<../.gitbook/assets/Screenshot 2021-01-06 at 2.22.49 PM.png>)

A new form will be created. Click on the "business registration form" new form.

![](<../.gitbook/assets/Screenshot 2021-01-06 at 2.28.13 PM.png>)

You will be redirected to the form editor page. Now, you can start setting it up, so that FormX can extract data from the other BR forms based on this form.

![](<../.gitbook/assets/Screenshot 2021-01-06 at 2.29.35 PM.png>)

## Set up the form

Now, we'll first go through a few concepts before marking areas on the master image.

### Anchors

An [_Anchor_](../features/labeller/anchor.md) is a labeled area that serves as a **positional reference point**, allowing FormX to warp uploaded images of a form. Since uploaded images are more or less different (e.g. a tilted angle) from the master image, FormX will have to twist them by matching their _Anchors _to the master form's ones before extracting.

For every form with a master image, **a user has to mark at least two **_**Anchors**_, with the longest distance possible between them. When they are further part, more of the form resides between them, which will improve extraction accuracy since the warping process becomes more consistent.&#x20;

**TL;DR:** Like an actual anchor, drop one on your master form to prevent future uploaded forms from moving away. **At least two are required for FormX to function properly.**

An example image is shown below, where two parts on a Business Registration form are marked as _Anchors_ - the "ORIGINAL" one and the title. We will go through anchor-marking in a later paragraph.

![](<../.gitbook/assets/Screenshot 2021-01-15 at 8.08.51 PM.png>)

You may be wondering: which parts in the master form should I mark with an _Anchor_? Identify the **common parts** of your form, then include them with an _Anchor_. Bear in mind that parts which vary across different documents of the same form should** not **be anchors.

#### Adding some to the master image

In the example, we'll mark three anchors which are the **common parts** of a BR form. Other areas like the actual name of business (i.e. KXX DXX TRANSPORTATION COMPANY) are different on every BR instance, so they **don't make good** anchors.

Choose the second tool as shown in the image below to mark an _Anchor_.

![](<../.gitbook/assets/Screenshot 2021-01-06 at 5.14.33 PM.png>)

Then mark points where the last connects with the first to create an _Anchor_, as shown in the GIF below.&#x20;

Note that only three _Anchors_ are marked here, while there exist other common parts that make good _Anchors _in a BR form, such as the field names "Name of Business/Corporation", "Business/Branch Name" and "Address". Don't confuse them with the field values though, as the field names don't change across BR forms while the values do.

![](../.gitbook/assets/ezgif-7-aaa61b2b35b0.gif)

The master form now has enough _Anchors _to warp properly.

### Detection Regions

_Detection Regions _are the areas that are marked from which you need data extracted. One _Detection Region _can have several extraction fields, as one region can contain several items of data that are worth obtaining or extracting.

**TL;DR:** Mark the area where you want information extracted from on the master form with _Detection Region._

#### Adding Detection Regions

In this example, we'll extract name of business, branch name and expiry date from BR forms. To do so, they will be marked with _Detection Regions_.

Choose the third tool marked with a red box in the screenshot below:

![](<../.gitbook/assets/Screenshot 2021-01-06 at 5.37.52 PM.png>)

As shown below, we'll add three _Detection Regions, _each containing a field called "name of business", "branch name", and "expiry date".

![](../.gitbook/assets/ezgif-7-036dabcfb491.gif)

Click the "Save" button. Now you've finished setting up this form!

## Test it out with other BR forms

There are two more BR forms in the ZIP file you've downloaded at the start of this tutorial. They will be fed to our freshly created form to have the target data extracted.

Navigate to the "Test" tab and choose `br_2_mobile_taken`. This will trigger an extraction which will complete in no time. Repeat these steps with the other image and you will get similar results.

![](../.gitbook/assets/ezgif-7-048fa1738870.gif)

As shown in the gif above, `br_2_mobile_taken` originally has a tilted angle but it's corrected and aligned once it's uploaded and warped. It was taken with a mobile phone with a not-so-perfect angle, still FormX manages to enhance such images "lesser" in quality and returns satisfactory results.&#x20;

## Integrating FormX with any app

By calling our APIs, extraction results can be obtained using any app. Navigate to the "API" tab, then copy both the form ID and your access token by clicking the buttons on the top right corner.&#x20;

Try calling the API with curl. Copy our curl example, replace the corresponding placeholders then press enter! With the correct payload given, you will promptly get the results. Simply translate this curl command to whatever language your app is built with, and you'll have got FormX easily integrated.

If you'd like to learn more about the APIs, we have a complete documentation in the "API" tab.

## Done!

You've now successfully extracted information from a set of documents that share the same format! One more [tutorial](set-up-a-form-without-master-image.md) to go!
