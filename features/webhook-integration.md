---
description: Integrate FormX with external systems using webhooks.
---

# Webhook Integration

After you upload the documents to FormX for extraction, FormX can send the results to a specified webhook URL. For example, you can connect it to Zapier and multiple services very easily.

### How to set it up

1. Go to **Integrations > Webhooks** in the portal
2. Click "**Add new webhook**".
3. Fill in a name for your reference. e.g. "My Webhook"
4. Enter the URL of your endpoint
5. Click "**Create**"
6. Under **"Connect with"**, select the forms and form groups you want to use.
7. Click "**Save**"

Now every time the form or the form group you choose has completed an extraction job, we will send a message with the extracted data to the URL endpoint.&#x20;

### Webhook delivery and Retries

The webhook handlers must respond with a status code within the `2xx` range within 10 seconds. Otherwise, it would be considered a failed delivery.

FormX will retry three more times with 30 minutes interval.
