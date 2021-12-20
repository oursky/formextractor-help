---
description: >-
  Detection Regions specify a user-defined region where data extraction(s) takes
  place.
---

# Detection Region

A user can specify an area with _Detection Region_ when data is needed from that part of the _Form._ A _Detection Region_ accepts multiple extraction fields, allowing you to extract several data items from an area.

![](<../../.gitbook/assets/Screenshot 2020-09-16 at 3.53.51 PM.png>)

The screenshot above shows a _Detection Region_ with three extraction fields: "chinese name", "english name" and "name" that contains the previous two. To filter out parts that are not needed(i.e. no Chinese in English name, and vice versa), they are both set to "Script" where some JavaScript is written to do the job. Since the "Name" field takes both the English and Chinese names, it can simply be set to "Block of English and Chinese".

Currently there are over 10 types available for an extraction field. You can also tweak with some advanced settings where you specify what OCR provider and API to use.
