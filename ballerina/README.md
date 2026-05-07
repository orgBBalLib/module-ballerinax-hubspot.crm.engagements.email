## Overview

[HubSpot](https://www.hubspot.com/) is a cloud-based customer relationship management (CRM) platform that helps businesses grow by providing tools for marketing, sales, customer service, and content management all in one place.

The `ballerinax/hubspot.crm.engagements.email` package offers APIs to connect and interact with [HubSpot CRM Engagements Email API](https://developers.hubspot.com/docs/api/crm/email) endpoints, specifically based on [HubSpot CRM API v3](https://developers.hubspot.com/docs/api/crm/overview).
## Setup guide

To use the HubSpot CRM Engagements Email connector, you must have access to the HubSpot API through a [HubSpot developer account](https://developers.hubspot.com/) and obtain an API access token. If you do not have a HubSpot account, you can sign up for one [here](https://app.hubspot.com/signup-hubspot/crm).

### Step 1: Create a HubSpot Account

1. Navigate to the [HubSpot website](https://www.hubspot.com/) and sign up for an account or log in if you already have one.

2. Note that while HubSpot offers a free CRM, certain API features and higher rate limits may require a Professional or Enterprise plan subscription. The Engagements API is available across plans, but some advanced functionality may be restricted based on your subscription tier.

### Step 2: Generate an API Access Token

HubSpot uses Private Apps to generate API access tokens. Follow these steps to create one:

1. Log in to your HubSpot account.

2. In the main navigation bar, click the **Settings** icon (gear icon) in the top right corner.

3. In the left sidebar menu, navigate to **Integrations** > **Private Apps**.

4. Click **Create a private app**.

5. On the **Basic Info** tab, provide a name and description for your app.

6. Navigate to the **Scopes** tab and select the required scopes for email engagements. You will need to enable scopes such as `crm.objects.contacts.read`, `crm.objects.contacts.write`, and `sales-email-read` depending on your use case.

7. Click **Create app** in the top right corner, then review the information and click **Continue creating**.

8. Copy the generated **Access token** displayed on the screen.

> **Tip:** You must copy and store this key somewhere safe. It won't be visible again in your account settings for security reasons.
## Quickstart

To use the `HubSpot CRM Engagements Email` connector in your Ballerina application, update the `.bal` file as follows:

### Step 1: Import the module

```ballerina
import ballerina/oauth2;
import ballerinax/hubspot.crm.engagements.email as hsemail;
```

### Step 2: Instantiate a new connector

1. Create a `Config.toml` file and configure the obtained credentials:

```toml
clientId = "<Your_Client_Id>"
clientSecret = "<Your_Client_Secret>"
refreshToken = "<Your_Refresh_Token>"
```

2. Create a `hsemail:ConnectionConfig` and initialize the client:

```ballerina
configurable string clientId = ?;
configurable string clientSecret = ?;
configurable string refreshToken = ?;

final hsemail:Client hsemailClient = check new ({
    auth: {
        clientId,
        clientSecret,
        refreshToken,
        credentialBearer: oauth2:POST_BODY_BEARER
    }
});
```

### Step 3: Invoke the connector operation

Now, utilize the available connector operations.

#### Create an email engagement

```ballerina
public function main() returns error? {
    hsemail:SimplePublicObjectInputForCreate newEmail = {
        associations: [],
        properties: {
            "hs_timestamp": "2024-01-15T10:30:00.000Z",
            "hs_email_subject": "Welcome to Our Service",
            "hs_email_text": "Thank you for signing up!",
            "hs_email_direction": "EMAIL"
        }
    };

    hsemail:SimplePublicObject response = check hsemailClient->/.post(newEmail);
}
```

### Step 4: Run the Ballerina application

```bash
bal run
```
## Examples

The `hubspot.crm.engagements.email` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples), covering the following use cases:

1. [Bulk update sender info](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/bulk_update_sender_info) - Demonstrates how to update sender information across multiple email engagements in bulk.
2. [Detect resend failed emails](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/detect_resend_failed_emails) - Illustrates how to identify and resend emails that previously failed to deliver.
3. [Email analytics reporting](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/email_analytics_reporting) - Shows how to generate analytics reports from email engagement data.