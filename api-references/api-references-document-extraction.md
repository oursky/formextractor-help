# Document Extraction

{% api-method method="post" host="https://worker.formextractorai.com" path="/extract-fields" %}
{% api-method-summary %}
Extract fields from the uploaded image
{% endapi-method-summary %}

{% api-method-description %}
This API support both submit as form, and upload the image in "multipart/form-data", or specify all parameters in HTTP Request Header and put image in the request body or X-WORKER-IMAGE-URL
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-WORKER-TOKEN" type="string" required=true %}
Access Token
{% endapi-method-parameter %}

{% api-method-parameter name="X-WORKER-FORM-ID" type="string" required=true %}
Form ID
{% endapi-method-parameter %}

{% api-method-parameter name="X-WORKER-IMAGE-URL" type="string" required=false %}
URL of the image to extract fields in JPG or PNG format, required if request body is empty
{% endapi-method-parameter %}

{% api-method-parameter name="X-WORKER-ENCODING" type="string" required=false %}
Encoding of the request body, 'raw' or 'base64'; Default value: 'raw'
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=false %}
\`image/jpeg\` or \`image/png\`, required if sent image content in the request body
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="form\_id" type="string" required=true %}
Form ID
{% endapi-method-parameter %}

{% api-method-parameter name="image" type="object" required=false %}
Image to extract in JPG or PNG format, either this parameter or image\_url are required
{% endapi-method-parameter %}

{% api-method-parameter name="image\_url" type="string" required=false %}
URL of image to extract in JPG or PNG format
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
status	String	"ok" if success
form_id	String	Form ID
fields	Field[]	List of extracted fields
Field.idoptional	string	Field ID (only appear in fields NOT belong in Detection Region)
Field.region_idoptional	string	Detection region ID (only appear in fields belong in Detection Region)
Field.label	string	Field label
Field.typeoptional	string	Field type (only appear in fields belong in Detection Region)
Field.languagesoptional	string[]	List of languages to support (only appear in fields NOT belong in Detection Region)
Field.content	any	Extracted content (For fields NOT belong to Detection Region, its type will always be string)
Field.erroroptional	string	Message of the error if exists
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

