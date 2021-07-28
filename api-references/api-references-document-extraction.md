# Document Extraction

## HTTP Endpoint

`POST https://worker.formextractorai.com/extract`

## Overview

Send the image with a `POST` request to the Extract API endpoint and FormX will isolate extraction fields from the uploaded image then perform OCR on these fields. 

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

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Optional</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Content-Type</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p><code>image/jpeg</code> or <code>image/png</code> or <code>application/pdf</code>
        </p>
        <p>*<b>required</b> if image is sent in the request body</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-TOKEN</td>
      <td style="text-align:left"><em>required</em>
      </td>
      <td style="text-align:left">
        <p>Access token</p>
        <p>This parameter must be included in the header.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-FORM-ID</td>
      <td style="text-align:left"><em>required</em>
      </td>
      <td style="text-align:left">Form ID</td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-IMAGE-URL</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">URL of the image, can be a JPG, PNG or PDF file
        <br />*<b>required</b> if request body is empty</td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-ENCODING</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Encoding of the request body, allowed &apos;raw&apos; or &apos;base64&apos;</p>
        <p>Default value: <code>raw</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-PDF-DPI</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>DPI of the uploaded pdf file</p>
        <p>Default value: <code>100</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-SHOW-CONFIDENCE</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for showing confidence score in response</p>
        <p>Default value: <code>false</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-AUTO-ADJUST-IMAGE-SIZE</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for auto adjusting image size for better extraction result, it will
          take a longer for extraction if enabled</p>
        <p>Default value: <code>true</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">X-WORKER-ASYNC</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for using the asynchronous mode</p>
        <p>Default value: <code>false</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Using parameters in form data

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Optional</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">form_id</td>
      <td style="text-align:left"><em>required</em>
      </td>
      <td style="text-align:left">Form ID</td>
    </tr>
    <tr>
      <td style="text-align:left">image</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>The image file, can be a JPG, PNG or PDF file</p>
        <p>Either specify this or provide the image_url parameter</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">image_url</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>URL of the image, can be a JPG, PNG or PDF file</p>
        <p>Either specify this or provide the image parameter</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">pdf_dpi</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>DPI of the uploaded pdf file</p>
        <p>Default value: <code>100</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">show_confidence</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for showing confidence score in response</p>
        <p>Default value: <code>false</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">auto_adjust_image_size</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for auto adjusting image size for better extraction result, it will
          take a longer for extraction if enabled</p>
        <p>Default value: <code>true</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">async</td>
      <td style="text-align:left"><em>optional</em>
      </td>
      <td style="text-align:left">
        <p>Flag for using the asynchronous mode</p>
        <p>Default value: <code>false</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## API Response

| Name | Type | Description |
| :--- | :--- | :--- |
| status | string | "ok" if success, "failed" if failed |
| form\_id | string | Form ID |
| fields | Field\[\] | List of extracted fields and fields in detection regions |
| auto\_extraction\_items | AutoExtractionItem\[\] | List of detected auto extraction items |
| key\_values | KeyValue\[\] | List of detected token groups |
| token\_groups | TokenGroup\[\] | List of detected token groups |
| error | any | Only exists if failed, its shape depends on the failure, but it always contain the "code" and "message" fields |

### Field

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">region_id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Detection region ID</td>
    </tr>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Field label</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Field type</td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left">any</td>
      <td style="text-align:left">Extracted content</td>
    </tr>
    <tr>
      <td style="text-align:left">error</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Message of the error if exists</td>
    </tr>
    <tr>
      <td style="text-align:left">confidence</td>
      <td style="text-align:left">number</td>
      <td style="text-align:left">
        <p>Confidence score
          <br />*exists if confidence score is enabled</p>
        <p>If there is a list of values, e.g. fields with the type name or address,
          this will be return alongside the value in the list.</p>
      </td>
    </tr>
  </tbody>
</table>

### AutoExtractionItem

| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | Item name |
| value | any | Item value |
| confidence | number | Confidence score \*exists if confidence score is enabled If there is a list of values, e.g. for name, address, and job\_title items, this will be return alongside the value in the list. |

### KeyValue

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">name</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Item name</td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Item value</td>
    </tr>
    <tr>
      <td style="text-align:left">confidence</td>
      <td style="text-align:left">number</td>
      <td style="text-align:left">
        <p>Confidence score</p>
        <p>*exists if confidence score is enabled</p>
      </td>
    </tr>
  </tbody>
</table>

### TokenGroup

| Name | Type | Description |
| :--- | :--- | :--- |
| name | string | Token group name |
| texts | Token\[\] | List of detected text tokens in this group |
| images | Token\[\] | List of detected image tokens in this group |

### Token

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">id</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Token id</td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Token value</td>
    </tr>
    <tr>
      <td style="text-align:left">confidence</td>
      <td style="text-align:left">number</td>
      <td style="text-align:left">
        <p>Confidence score</p>
        <p>*exists if confidence score is enabled</p>
      </td>
    </tr>
  </tbody>
</table>

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

```text
201 Created {
   status: "pending"
}
```

#### Completed

```text
200 OK {
   status: "OK",
   pages: [
       // structure same as the extract API
   ]
}
```

