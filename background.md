---
description: >-
  Covers basic concepts of FormX. Practical tips will be provided at later
  sections.
---

# Basics

## What is FormX?

FormX is a data extraction service, transforming analogue information on physical documents to digital structured JSON values. By uploading an image copy of document that you'd like to extract data from, specifying what are your targets, in no time FormX will return them in JSON format, ready to be integrated.

So what's so special about FormX? Pulling data off documents is solved long ago by OCR readers. While OCR is already a mature technology, it can only extract data aimlessly. OCR can definitely obtain all information from a document, but it can't:

* differentiate between data pairs
* retrieve user-defined targets
* label targets before returning in a development-friendly format - JSON

**FormX does possess the above abilities**, by implementing a series of Artificial Intelligence models. In other words, on top of some popular OCR services, we have applied an AI layer when data filtering, locating, grouping and labelling are carried out, before the processed data is passed back to the user in JSON format.

## How can FormX be used?

There are two main scenarios FormX can solve. Both scenarios require some quick set up. For the time being, _Form_ creation and all set up tasks can only be carried out on our [portal](https://formextractor.oursky.com/form). Meanwhile, extractions can be done on the portal, our desktop apps or via APIs, where you can submit photo copies of documents and receive results.

To quickly sum up the roles of these three platforms:

* Portal - its functionality includes form set up, management on payment and access token, download desktop app and test out sample images one by one.
* Desktop app - available on both Windows and Mac, designed to batch upload and process form images.
* API - the natural way to integrate FormX with your apps.

Before we dive in to the scenarios, it's crucial to understand what's a _Form_ in FormX.

### What is a _Form_?

A _Form_ represents a format of document. By creating and configuring a _Form_, a user passes a set of instructions about a specific form format to FormX, which will be used to extract information from forms with such format.

Guides on using the portal and setting up a _Form_ are covered in later tutorials, for now you only have to understand the concepts.

### 1 - Data extraction from a set of documents with the same format

The user will first need to create a _form_, upload a _master image_ then set it up by specifying extraction requirements and labelling target areas. FormX will then learn \(i.e. compute features\) from this _form_, and future data extractions will be executed based on these learnings. 

In short, the user _tells_ FormX about the format of incoming documents, so that FormX _understands_ which areas and what data to extract from upload images.

**TL;DR:** works for any set of documents, **with the same format**.

**Examples:** insurance forms, bank statements, licences, certificates issued by government bodies etc.

### 2 - Data extraction from all kinds of documents with Auto Extraction Items

Unlike the other scenario, no _master image_ is needed. FormX offers a list of [Auto Extraction Items](features/auto-extraction-items.md), which are a bunch of targets that can be pulled off different types of documents.

FormX already has corresponding AI models trained, as a result all a user has to do is create a _form_ and tick the targets from the list of Auto Extraction Items. 

Say you want to get the date from a pile of receipts, tick the date box under the list of Auto Extraction Items on FormX's portal. You can then upload image copies of the receipts and have their date extracted.

**TL;DR:** extraction a specific data target from any documents, **as long as FormX supports that target**.

**Examples:** receipts, tickets \(e.g. flight, train, movie\), bank statements if only available targets needed

### Explaining with examples

To aid grasping these ideas, let's go through a few examples. Say you have 3 types of documents and they extraction targets are:

1. A pile of **driving licences** with same format - **name, address, age**
2. A pile of **business registration** documents, same format - **company name, issue date, address**
3. A stack of **receipts** from different shops - **date, time, price**

whose data is needed on your system and you aim to automate the extraction process with FormX. In this case, you will need creating three forms on FormX's portal. 

Since 1 and 2 both have a format to follow, they lie in the first scenario. As a result, they share the same set up flow:

* First pick a member out of the pile with a clear resolution
* Create a _Form_ and upload that member as the master image
* Set up the _Form_ with tools on our portal, e.g. labelling areas, specifying target data
* Save!

Documents of type 3 are issued by a range of shops so they don't share a format. Therefore the set up flow is bit different:

* Create a _Form_ with no master image
* Specify Auto Extraction Items
* Save!

That's all and now the three forms are ready for their own document data extraction.

### Tutorial time!

Each scenario has its own get started tutorial. After finishing them you will become familiar with how FormX's use cases!

**Scenario 1 Tutorial:** [Set up a form with master image](get-started/set-up-a-form-with-master-image.md)

**Scenario 2 Tutorial:** [Set up a form without master image](get-started/set-up-a-form-without-master-image.md)

