---
description: >-
  Auto Extraction Items are targets that are searched throughout every document,
  independent from the master image.
---

# Auto Extraction Items

## A quick guide

Auto Extraction Items are created to extract specific targets from documents that don't share a format, like receipts, tickets and invoices. 

To configure the list of targets you're seeking, navigate to the "Setting" tab in the Form's editor and check the ones you need. Available items depend on the "Document Type", as shown in the following mapping:

**General**

* Date
* Time
* Name
* Address

**Receipt**

* Total Amount
* Date
* Time
* Address

**Bank Statement**

* Name
* Address
* Date

For example, if you have the date ticked, FormX will attempt to return the best candidate it can find from uploaded image.

This [tutorial](../get-started/set-up-a-form-without-master-image.md) covers how Auto Extraction Items work when there's no master image. Note that Auto Extraction Items are not bound to Forms with no master image, they can be ticked in Forms with master image as well!

