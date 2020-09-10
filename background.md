# Background

## What is FormX?

FormX is a data extraction service, transforming analogue information on physical documents to digital structured JSON values. By uploading an image copy of document that you'd like to extract data from, specifying what are your targets, in no time FormX will return them in JSON format, ready to be integrated.

So what's so special about FormX? Pulling data off documents is solved long ago by OCR readers. While OCR is already a mature technology, it can only extract data aimlessly. OCR can definitely obtain all information from a document, but it can't:

* differentiate between data pairs
* retrieve user-defined targets
* label targets before returning in a development-friendly format - JSON

**FormX does possess the above abilities**, by implementing a series of Artificial Intelligence models. In other words, on top of some popular OCR services, we have applied an AI layer when data filtering, locating, grouping and labelling are carried out, before the processed data is passed back to the user in JSON format.

## How can FormX be used?

There are two main scenarios FormX can solve. Both scenarios require some quick set up. For the time being, all set up tasks can only be carried out on our [portal](https://formextractor.oursky.com/form). Meanwhile, extractions can be done on the portal, via APIs or our desktop apps.

Each scenario has a get started tutorial where details are further discussed there.

### Data extraction from a set of documents with the same format

The user will first need to create a _form_, upload a _master image_ then set it up by specifying extraction requirements and labelling target areas. FormX will then learn \(i.e. compute features\) from this _form_, and future data extractions will be executed based on these learnings. 

In short, the user _tells_ FormX about the format of incoming documents, so that FormX _understands_ which areas and what data to extract from upload images.

**TL;DR:** works for any set of documents, **with the same format**.

**Examples:** insurance forms, bank statements, licences, certificates issued by government bodies etc.

**Tutorial:** [Set up a form with master image](get-started/set-up-a-form-with-master-image.md)

### Data extraction from all kinds of documents with Auto Extraction Items

Unlike the other scenario, no _master image_ is needed. FormX offers a list of [Auto Extraction Items](features/auto-extraction-items.md), which are a bunch of targets that can be pulled off different types of documents.

FormX already has corresponding AI models trained, as a result all a user has to do is create a _form_ and tick the targets from the list of Auto Extraction Items. 

Say you want to get the date from a pile of receipts, tick the date box under the list of Auto Extraction Items on FormX's portal. You can then upload image copies of the receipts and have their date extracted.

**TL;DR:** extraction a specific data target from any documents, **as long as FormX supports that target**.

**Examples:** receipts, tickets \(e.g. flight, train, movie\), bank statements if only available targets needed

**Tutorial:** [Set up a form without master image](get-started/set-up-a-form-without-master-image.md)





