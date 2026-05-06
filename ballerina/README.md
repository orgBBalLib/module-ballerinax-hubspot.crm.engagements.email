## Overview

[HubSpot](https://www.hubspot.com/) is a cloud-based customer relationship management (CRM) platform that helps businesses grow by providing tools for marketing, sales, customer service, and content management, all powered by a unified customer database.

The `ballerinax/hubspot.crm.engagements.email` package offers APIs to connect and interact with [HubSpot CRM Engagements Emails API](https://developers.hubspot.com/docs/api/crm/email) endpoints, specifically based on [HubSpot CRM API v3](https://developers.hubspot.com/docs/api/crm/email).
## Setup guide

To use the HubSpot CRM Engagements Email connector, you must have access to the HubSpot API through a [HubSpot developer account](https://developers.hubspot.com/) and obtain an API access token. If you do not have a HubSpot account, you can sign up for one [here](https://app.hubspot.com/signup-hubspot/crm).

### Step 1: Create a HubSpot Account

1. Navigate to the [HubSpot website](https://www.hubspot.com/) and sign up for an account or log in if you already have one.

2. If you intend to use API keys, note that HubSpot API keys are only available on accounts with a Marketing Hub, Sales Hub, Content Hub, Operations Hub, or Service Hub Professional or Enterprise plan. For development and testing purposes, you can create a [HubSpot developer account](https://developers.hubspot.com/get-started) which provides access to test portals.

### Step 2: Generate an API Access Token

HubSpot recommends using Private Apps to generate access tokens for API authentication.

1. Log in to your HubSpot account.

2. In the main navigation bar, click the **Settings** icon (gear icon) in the top right corner.

3. In the left sidebar menu, navigate to **Integrations** > **Private Apps**.

4. Click **Create a private app**.

5. On the **Basic Info** tab, enter a name and description for your app.

6. Navigate to the **Scopes** tab and select the required scopes for the CRM Engagements Email API, including `crm.objects.contacts.read`, `crm.objects.contacts.write`, `sales-email-read`, and other relevant engagement scopes.

7. Click **Create app** in the top right corner, then review the information and click **Continue creating**.

8. Once the private app is created, your access token will be displayed. Click **Show token** to reveal and copy it.

> **Tip:** You must copy and store this key somewhere safe. It won't be visible again after you navigate away from the page for security reasons.
## Quickstart

To use the `HubSpot CRM Engagements Email` connector in your Ballerina application, update the `.bal` file as follows:

### Step 1: Import the module

```ballerina
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
        refreshToken
    }
});
```

### Step 3: Invoke the connector operation

Now, utilize the available connector operations.

#### Create a new email engagement

```ballerina
public function main() returns error? {
    hsemail:SimplePublicObjectInputForCreate newEmail = {
        associations: [],
        properties: {
            "hs_timestamp": "2024-01-15T10:30:00.000Z",
            "hs_email_subject": "Follow-up on your inquiry",
            "hs_email_text": "Thank you for reaching out. We would love to discuss further.",
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