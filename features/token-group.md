---
description: >-
  Tokens added will be searched throughout uploaded documents, either a text
  string or image.
---

# Token Group

## A quick guide

Token group was originally designed and developed to differentiate receipts by user specified inputs.

Say you have N possible shops issuing receipts and you'd like to distinguish which receipt belongs to which shop. To do that you can navigate to a Form, switch to the "Token Group" tab and:

1. Create a token group called "Shop Names". Then input the N shop names.
2. Create another token group called "Shop Icons" and upload the N shop icons.
3. Don't forget click save!

Then throw in some receipts and have the tokens matched.

## Here comes some samples

We understand it can be hard to grasp the idea without actually trying out and it can be a challenge to gather a bunch of receipts in a short time. Here's a set of Uniqlo \(some clothing brand that's quite popular here in Hong Kong\) [receipts](https://drive.google.com/drive/folders/1Aoo5IP-26rhZztlx3w710GtP2ctXIA42?usp=sharing). Click download where one will be triggered with the content zipped. Uncompress the downloaded file and you will get a directory that looks like:

```text
.
├── icons
│   ├── uniqlo_en.png
│   └── uniqlo_jp.png
├── receipt_uniqlo_1.jpg
├── receipt_uniqlo_2.jpg
├── receipt_uniqlo_3.jpg
└── receipt_uniqlo_4.jpg
```

Then we will add one text token and two image tokens:

1. Create a token group called "Shop Names" and add a text token named `uniqlo` which is on all samples you have just downloaded.
2. Create another token group called "Shop Icons". Inside the unzipped folder you have downloaded there is an icon subfolder. Upload the two images inside - `uniqlo_en.png` and `uniqlo_jp.png` under the newly created image token group, and named them from their file name.
3. Remember to save!

Now, navigate to the "Test" tab and pull downloaded samples in one by one. You will see all three tokens we have added just now are showing up in the result, as shown in this screenshot:

![](../.gitbook/assets/screenshot-2020-09-15-at-5.42.38-pm.png)

The JSON output indicates the tokens are matched as well:

```text
{
  "status": "ok",
  "form_id": "some_id",
  "fields": [],
  "auto_extraction_items": [
    {
      "name": "total_amount",
      "value": 308
    },
    {
      "name": "date",
      "value": "09/09/2019"
    },
    {
      "name": "time",
      "value": "15:15:00"
    }
  ],
  "token_groups": [
    {
      "id": "some_id",
      "name": "shop name",
      "texts": [
        {
          "id": "some_id",
          "value": "uniqlo"
        }
      ]
    },
    {
      "id": "some_id",
      "images": [
        {
          "id": "some_id",
          "value": "uniqlo_en"
        },
        {
          "id": "some_id",
          "value": "uniqlo_jp"
        }
      ],
      "name": "shop icon"
    }
  ]
}
```

The matched tokens are returned in their own token group, labelled and structured.

