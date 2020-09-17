---
description: >-
  Receipts and tickets often have fields like total amount, issue date and time,
  that are the usual targets for data capture and extraction. FormX offers a
  list of Auto Extraction Items to achieve that.
---

# Receipts or Tickets

## How does FormX fit in?

In every [Form](background.md#what-is-formx) on FormX, there is a list of [Auto Extraction Items](features/auto-extraction-items.md) to choose from. By ticking one of them, for example, address, FormX will perform a search in uploaded images for anything that looks like an address \(according to our AI models\) and yield a result if one is located.

There's often the need to differentiate receipts and invoices by shop, which is why FormX comes with [Token Group](features/token-group.md). You can specify what tokens \(either a string or image\) you're seeking in a document, and FormX will attempt to locate them and report afterward if any is found. Please refer to the Token Group link for further details.

## Use cases and success stories

### Receipts

Various shopping malls wished to establish a loyalty program with receipts where information on date, time and total price are needed. By plugging FormX  into their pipeline, customers can simply have their receipts scanned and receive loyalty points once data is extracted and processed.

### Bank statements

Bank applications require proof of address, and FormX has the capability to recognize and process address information from bank statements.

## Try them out!

We do provide a receipt template, and in every [_Form_](background.md#what-is-a-form)_'s_ "Settings" tab you can set its document type to "Receipt" or "Bank Statement" where a combination of Auto Extraction Items will be selected for you automatically. You can then test with uploading an image.

