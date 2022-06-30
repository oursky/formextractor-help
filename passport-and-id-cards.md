---
description: >-
  You can use FormX to extract information from identity documents such as
  passports, ID cards and driver's license.
---

# Passport & ID Cards

### List of supported Countries and ID

| Country       | Type                         |
| ------------- | ---------------------------- |
| All countries | Passport                     |
| Hong Kong     | Identity Card                |
| Taiwan        | National Identification Card |
| Macau         | Identity Card                |
| Singapore     | NRIC, Work passes            |

{% hint style="info" %}
This is a growing list. [Contact us](https://www.formx.ai/talk-with-us) if the ID you need is not listed here.
{% endhint %}

### How to use

1. Select **International ID** from the side bar in the portal.
2. Test your photos by uploading them to the "Test" tab.
3. Copy "Access Token" and "Form ID" to use the extractor via RESTful API. See [API Reference](api-references/api-references-document-extraction.md).

### Attributes

These are the attributes that are extracted from the identity documents. The attributes that are unavailable from the documents will not be returned.

| Attribute name                                                    | Meaning                                                                              | Value                                                                            |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| type\_of\_id                                                      | The type of document                                                                 | type.country.subdivision e.g. \`id.hkg\` , \`driverslicense.usa.ny\` , \`other\` |
| name                                                              | Full name of the holder                                                              | String, Variable length in latin script                                          |
| surname                                                           | Surname/Family name of the holder                                                    | String, Variable length in latin script                                          |
| given\_names                                                      | Given names of the holder                                                            | String, Variable length in latin script                                          |
| <p>name-(two letter lang code) <br>e.g. name-zh / name-ko</p>     | Name of the holder in non-latin script                                               | String, Variable length in non-latin script                                      |
| <p>surname-(two letter lang code) <br>e.g. surname-zh</p>         | Surname/Family name of the holder in non-latin script                                | String, Variable length in non-latin script                                      |
| <p>given_names-(two letter lang code) <br>e.g. given_names-zh</p> | given names of the holder in non-latin script                                        | String, Variable length in non-latin script                                      |
| date\_of\_birth                                                   | Date of birth of the holder                                                          | YYYY-MM-DD or YYYY-MM or YYYY                                                    |
| date\_of\_issue                                                   | Issue date of the document                                                           | YYYY-MM-DD                                                                       |
| date\_of\_expiry                                                  | Expiry date of the document                                                          | YYYY-MM-DD                                                                       |
| sex                                                               | Sex or gender of the holder                                                          | M, F, or X                                                                       |
| place\_of\_birth                                                  | City or State of the holder’s birthplace                                             | String, Variable length                                                          |
| nationality                                                       | Nationality of the holder as printed on the document                                 | String, Variable length                                                          |
| nationality\_code                                                 | Nationality of the holder in 3-letter code as defined in ICAO Doc 9303-3             | String, three letters                                                            |
| issuing\_authority                                                | Issuing organization of the document as printed in the document                      | String, Variable length                                                          |
| personal\_number                                                  | Personal identification number given to holder by the issuing State or organization. | String, Variable length e.g. HKID number: A123456(7)                             |
| document\_number                                                  | The number given by the issuer to identify the document                              | String, Variable length                                                          |
| portrait                                                          | The bounding box of the portrait of the holder                                       | Array \[x1,y1,x2,y2]                                                             |
| signature                                                         | The bounding box of the signature of the holder                                      | Array \[x1,y1,x2,y2]                                                             |
| address                                                           | Address of the holder                                                                | String, Variable length                                                          |
| postal\_code                                                      | Postal code of the holder                                                            | String, Variable length                                                          |
