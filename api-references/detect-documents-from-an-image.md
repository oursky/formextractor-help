---
description: >-
  FormX will detect documents such as ID card and receipt from the uploaded
  image. It will return the bounding box and type of each detected document.
---

# Detect documents from an image

## API Endpoint

```
POST https://worker.formextractorai.com/detect-documents
```

### cURL Example

```bash
curl -X POST \
https://worker.formextractorai.com/detect-documents \
-H 'Content-Type: image/jpeg' \
-H 'X-WORKER-TOKEN: REPLACE-YOUR-WORKER-TOKEN-HERE' \
--data-binary "@/path/to/query/image.jpg"
```

### Option 1: Send image over body

The simplest way is to send the image content in the body as raw binary data or base64, and send the parameters in the header

#### Parameters in Header

| Header            | Description                                                                                                              | Required? |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------ | --------- |
| Content-Type      | `image/jpeg` or `image/png` or `application/pdf`                                                                         | required  |
| X-WORKER-TOKEN    | Access token                                                                                                             | required  |
| X-WORKER-ENCODING | <p>Encoding of the request body, allowed <code>raw</code> or <code>base64</code> <br>Default value: <code>raw</code></p> | optional  |
| X-WORKER-PDF-DPI  | <p>DPI of the uploaded pdf file.<br>Default value: <code>100</code></p>                                                  | optional  |

### Option 2: Send image over form-data

You can also send the image file in multipart/form-data.

#### Parameters in Header

| Name           | Description           | Required? |
| -------------- | --------------------- | --------- |
| Content-Type   | `multipart/form-data` | required  |
| X-WORKER-TOKEN | Access token          | required  |

#### Parameters in Body form-data

| Name     | Description                                                              | Required? |
| -------- | ------------------------------------------------------------------------ | --------- |
| image    | Image to detect documents in jpg or png format, or a pdf file.           | required  |
| pdf\_dpi | <p>DPI of the uploaded pdf file. <br>Default value: <code>100</code></p> | optional  |

### Option 3: Send image by URL

Instead of attaching the image file in the request, you can also specify the URL to the image. Either send it in the header or in the body as multipart/form-data.

#### Parameters in Header

| Name               | Description                                                                 | Required?                                                                  |
| ------------------ | --------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| X-WORKER-TOKEN     | Access token                                                                | required                                                                   |
| X-WORKER-IMAGE-URL | URL of the image to be processed in jpg or png format, or URL of a pdf file | Specify the URL here or in form-data                                       |
| X-WORKER-PDF-DPI   | <p>DPI of the uploaded pdf file. <br>Default value: <code>100</code></p>    | Optional, only applicable if the URL in `X-WORKER-IMAGE-URL` is a pdf file |

#### Parameters in Body form-data

| Name       | Description                                                                 | Required?                                                         |
| ---------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| image\_url | URL of the image to be processed in jpg or png format, or URL of a pdf file | Specify the URL here or in the Header                             |
| pdf\_dpi   | <p>DPI of the uploaded pdf file. <br>Default value: <code>100</code></p>    | Optional, only applicable if the URL in `image_url` is a pdf file |

### Response

| Key       | Type        | Description                                                                                                 |
| --------- | ----------- | ----------------------------------------------------------------------------------------------------------- |
| status    | string      | "ok" if success                                                                                             |
| error     | any         | Only exists if failed, its shape depends on the failure, but it will always has "code" and "message" fields |
| documents | Document\[] | List of detected documents                                                                                  |

#### Document

The document is returned in the `documents` array.

|             |           |                                                                                                               |
| ----------- | --------- | ------------------------------------------------------------------------------------------------------------- |
| bbox        | number\[] | Bounding box of the detected document in `[x1, y1, x2, y2]`                                                   |
| bbox\_score | number    | Confidence score of the detected bounding box                                                                 |
| type        | string    | Type of the detected document. [See below.](detect-documents-from-an-image.md#type-of-the-document-supported) |
| type\_score | number    | Confidence score of the detected type                                                                         |

## Type of the documents supported

Here is the list of documents can be detected by FormX

* Passport (Personal data page): `passport_id`
* ID cards: `id_card`
* Receipts/Invoices: `receipt`
* Others: `general`

{% hint style="info" %}
This is a growing list. [Contact us](https://www.formx.ai/talk-with-us) if the document type you need is not here!
{% endhint %}
