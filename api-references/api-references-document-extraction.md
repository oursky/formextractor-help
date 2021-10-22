# Document Extraction

## HTTP Endpoint

`POST https://worker.formextractorai.com/extract`

## Overview

Send the image with a `POST` request to the Extract API endpoint and FormX will isolate extraction fields from the uploaded image then perform OCR on these fields.&#x20;

FormX will use the form model of your choice to extract and return the data in a JSON format. The form model can be specified by the `form_id` parameter. An Access Token should also be included. They can be obtained from the web portal dashboard.

FormX provides two modes to access the API, synchronous or asynchronous, which can be specified by a parameter. [See more details below](api-references-document-extraction.md#using-the-asynchronous-mode).

### cURL Example

```bash
curl -X POST \
https://worker.formextractorai.com/extract \
-H 'Content-Type: image/jpeg' \
-H 'X-WORKER-FORM-ID: REPLACE-YOUR-FORM-ID-HERE' \
-H 'X-WORKER-TOKEN: REPLACE-YOUR-WORKER-TOKEN-HERE' \
--data-binary "@/path/to/query/image.jpg"
```

## Making the Request

If you want to upload the image directly, it can be uploaded in the request body or via multipart/form-data. If you want to specify an image url, it can be submitted via a header or multipart/form-data.

Most of the parameters can be submitted either as multipart/form-data or as request headers.

#### Using parameters in HTTP request headers

| Name                            | Optional   | Description                                                                                                                                                    |
| ------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Content-Type                    | _optional_ | <p><code>image/jpeg</code> or <code>image/png</code> or <code>application/pdf</code></p><p>*<strong>required</strong> if image is sent in the request body</p> |
| X-WORKER-TOKEN                  | _required_ | <p>Access token</p><p>This parameter must be included in the header.</p>                                                                                       |
| X-WORKER-FORM-ID                | _required_ | Form ID                                                                                                                                                        |
| X-WORKER-IMAGE-URL              | _optional_ | <p>URL of the image, can be a JPG, PNG or PDF file<br>*<strong>required</strong> if request body is empty</p>                                                  |
| X-WORKER-ENCODING               | _optional_ | <p>Encoding of the request body, allowed 'raw' or 'base64'</p><p>Default value: <code>raw</code></p>                                                           |
| X-WORKER-PDF-DPI                | _optional_ | <p>DPI of the uploaded pdf file</p><p>Default value: <code>100</code></p>                                                                                      |
| X-WORKER-SHOW-CONFIDENCE        | _optional_ | <p>Flag for showing confidence score in response</p><p>Default value: <code>false</code></p>                                                                   |
| X-WORKER-AUTO-ADJUST-IMAGE-SIZE | _optional_ | <p>Flag for auto adjusting image size for better extraction result, it will take a longer for extraction if enabled</p><p>Default value: <code>true</code></p> |
| X-WORKER-ASYNC                  | _optional_ | <p>Flag for using the asynchronous mode</p><p>Default value: <code>false</code></p>                                                                            |

#### Using parameters in form data

| Name                      | Optional   | Description                                                                                                                                                    |
| ------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| form\_id                  | _required_ | Form ID                                                                                                                                                        |
| image                     | _optional_ | <p>The image file, can be a JPG, PNG or PDF file</p><p>Either specify this or provide the image_url parameter</p>                                              |
| image\_url                | _optional_ | <p>URL of the image, can be a JPG, PNG or PDF file</p><p>Either specify this or provide the image parameter</p>                                                |
| pdf\_dpi                  | _optional_ | <p>DPI of the uploaded pdf file</p><p>Default value: <code>100</code></p>                                                                                      |
| show\_confidence          | _optional_ | <p>Flag for showing confidence score in response</p><p>Default value: <code>false</code></p>                                                                   |
| auto\_adjust\_image\_size | _optional_ | <p>Flag for auto adjusting image size for better extraction result, it will take a longer for extraction if enabled</p><p>Default value: <code>true</code></p> |
| async                     | _optional_ | <p>Flag for using the asynchronous mode</p><p>Default value: <code>false</code></p>                                                                            |

## API Response

| Name                    | Type                  | Description                                                                                                    |
| ----------------------- | --------------------- | -------------------------------------------------------------------------------------------------------------- |
| status                  | string                | "ok" if success, "failed" if failed                                                                            |
| form\_id                | string                | Form ID                                                                                                        |
| fields                  | Field\[]              | List of extracted fields and fields in detection regions                                                       |
| auto\_extraction\_items | AutoExtractionItem\[] | List of detected auto extraction items                                                                         |
| key\_values             | KeyValue\[]           | List of detected token groups                                                                                  |
| token\_groups           | TokenGroup\[]         | List of detected token groups                                                                                  |
| error                   | any                   | Only exists if failed, its shape depends on the failure, but it always contain the "code" and "message" fields |

### Field

| Name       | Type   | Description                                                                                                                                                                                           |
| ---------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| region\_id | string | Detection region ID                                                                                                                                                                                   |
| name       | string | Field label                                                                                                                                                                                           |
| type       | string | Field type                                                                                                                                                                                            |
| value      | any    | Extracted content                                                                                                                                                                                     |
| error      | string | Message of the error if exists                                                                                                                                                                        |
| confidence | number | <p>Confidence score<br>*exists if confidence score is enabled</p><p>If there is a list of values, e.g. fields with the type name or address, this will be return alongside the value in the list.</p> |

### AutoExtractionItem

| Name       | Type   | Description                                                                                                                                                                                          |
| ---------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name       | string | Item name                                                                                                                                                                                            |
| value      | any    | Item value                                                                                                                                                                                           |
| confidence | number | <p>Confidence score<br>*exists if confidence score is enabled<br>If there is a list of values, e.g. for name, address, and job_title items, this will be return alongside the value in the list.</p> |

### KeyValue

| Name       | Type   | Description                                                          |
| ---------- | ------ | -------------------------------------------------------------------- |
| name       | string | Item name                                                            |
| value      | string | Item value                                                           |
| confidence | number | <p>Confidence score</p><p>*exists if confidence score is enabled</p> |

### TokenGroup

| Name   | Type     | Description                                 |
| ------ | -------- | ------------------------------------------- |
| name   | string   | Token group name                            |
| texts  | Token\[] | List of detected text tokens in this group  |
| images | Token\[] | List of detected image tokens in this group |

### Token

| Name       | Type   | Description                                                          |
| ---------- | ------ | -------------------------------------------------------------------- |
| id         | string | Token id                                                             |
| value      | string | Token value                                                          |
| confidence | number | <p>Confidence score</p><p>*exists if confidence score is enabled</p> |

## Using the Asynchronous mode

If the request takes too long to complete, you can use the asynchronous mode to avoid timeout. This can be enabled by the `async` parameter either in the header or form data.

### Job ID

If the async job is successfully created, a `202 Accepted` response will be returned with the `job_id` and the `page_count`.

```http
202 Accepted {
  async: true,
  job_id: <string>,
  page_count: <number>,
}
```

### Getting the extraction result

`GET https://worker.formextractorai.com/extract/jobs/:job_id`

The extraction result can be queried by polling the Job endpoint. Send `GET` request to the endpoint `/extract/jobs/:job_id` with the access token in the header until the result is returned.

The extraction result will be deleted 24 hours after the job is completed, no matter it has been queried or not.

#### Pending

```
201 Created {
   status: "pending"
}
```

#### Completed

```
200 OK {
   status: "OK",
   pages: [
       // structure same as the extract API
   ]
}
```
