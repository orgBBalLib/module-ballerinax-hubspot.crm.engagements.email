
# Ballerina hubspot.crm.engagements.email connector

[![Build](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/ci.yml/badge.svg)](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/ci.yml)
[![Trivy](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/trivy-scan.yml/badge.svg)](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/trivy-scan.yml)
[![GraalVM Check](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/build-with-bal-test-graalvm.yml/badge.svg)](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/actions/workflows/build-with-bal-test-graalvm.yml)
[![GitHub Last Commit](https://img.shields.io/github/last-commit/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email.svg)](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/commits/master)
[![GitHub Issues](https://img.shields.io/github/issues/ballerina-platform/ballerina-library/module/hubspot.crm.engagements.email.svg?label=Open%20Issues)](https://github.com/ballerina-platform/ballerina-library/labels/module%hubspot.crm.engagements.email)

## Overview

[HubSpot](https://www.hubspot.com/) is a cloud-based customer relationship management (CRM) platform that helps businesses attract, engage, and delight customers through integrated marketing, sales, service, and content management tools.

The `ballerinax/hubspot.crm.engagements.email` package offers APIs to connect and interact with [HubSpot CRM Engagements Email API](https://developers.hubspot.com/docs/api/crm/email) endpoints, specifically based on [HubSpot CRM API v3](https://developers.hubspot.com/docs/api/crm/overview).
## Setup guide

To use the HubSpot CRM Engagements Email connector, you must have access to the HubSpot API through a [HubSpot developer account](https://developers.hubspot.com/) and obtain an API access token. If you do not have a HubSpot account, you can sign up for one [here](https://app.hubspot.com/signup-hubspot/crm).

### Step 1: Create a HubSpot Account

1. Navigate to the [HubSpot website](https://www.hubspot.com/) and sign up for an account or log in if you already have one.

2. Note that while HubSpot offers a free CRM tier, certain API features and higher rate limits may require a Professional or Enterprise plan subscription. Review the [HubSpot pricing page](https://www.hubspot.com/pricing) to ensure your plan supports the API functionality you need.

### Step 2: Generate an API Access Token

HubSpot uses private apps to generate access tokens for API authentication. Follow these steps to create a private app and obtain your access token:

1. Log in to your HubSpot account.

2. In the main navigation bar, click the **Settings** icon (gear icon) in the top right corner.

3. In the left sidebar menu, navigate to **Integrations** > **Private Apps**.

4. Click **Create a private app**.

5. On the **Basic Info** tab, enter a name and description for your app.

6. Navigate to the **Scopes** tab and select the required scopes for the CRM Engagements Email API. At minimum, enable scopes such as `crm.objects.contacts.read`, `crm.objects.contacts.write`, and `sales-email-read` depending on your integration needs.

7. Click **Create app** in the top right corner, then review and click **Continue creating** to confirm.

8. Once the app is created, your access token will be displayed. Click **Show token** to reveal it.

> **Tip:** You must copy and store this key somewhere safe. It won't be visible again without regenerating, and regenerating will invalidate the previous token.
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
            "hs_email_direction": "EMAIL",
            "hs_email_subject": "Follow-up on our meeting",
            "hs_email_text": "Thank you for meeting with us today."
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
## Build from the source

### Setting up the prerequisites

1. Download and install Java SE Development Kit (JDK) version 21. You can download it from either of the following sources:

    * [Oracle JDK](https://www.oracle.com/java/technologies/downloads/)
    * [OpenJDK](https://adoptium.net/)

    > **Note:** After installation, remember to set the `JAVA_HOME` environment variable to the directory where JDK was installed.

2. Download and install [Ballerina Swan Lake](https://ballerina.io/).

3. Download and install [Docker](https://www.docker.com/get-started).

    > **Note**: Ensure that the Docker daemon is running before executing any tests.

4. Export Github Personal access token with read package permissions as follows,

    ```bash
    export packageUser=<Username>
    export packagePAT=<Personal access token>
    ```

### Build options

Execute the commands below to build from the source.

1. To build the package:

    ```bash
    ./gradlew clean build
    ```

2. To run the tests:

    ```bash
    ./gradlew clean test
    ```

3. To build the without the tests:

    ```bash
    ./gradlew clean build -x test
    ```

4. To run tests against different environments:

    ```bash
    ./gradlew clean test -Pgroups=<Comma separated groups/test cases>
    ```

5. To debug the package with a remote debugger:

    ```bash
    ./gradlew clean build -Pdebug=<port>
    ```

6. To debug with the Ballerina language:

    ```bash
    ./gradlew clean build -PbalJavaDebug=<port>
    ```

7. Publish the generated artifacts to the local Ballerina Central repository:

    ```bash
    ./gradlew clean build -PpublishToLocalCentral=true
    ```

8. Publish the generated artifacts to the Ballerina Central repository:

    ```bash
    ./gradlew clean build -PpublishToCentral=true
    ```

## Contribute to Ballerina

As an open-source project, Ballerina welcomes contributions from the community.

For more information, go to the [contribution guidelines](https://github.com/ballerina-platform/ballerina-lang/blob/master/CONTRIBUTING.md).

## Code of conduct

All the contributors are encouraged to read the [Ballerina Code of Conduct](https://ballerina.io/code-of-conduct).


## Useful links

* For more information go to the [`hubspot.crm.engagements.email` package](https://central.ballerina.io/ballerinax/hubspot.crm.engagements.email/latest).
* For example demonstrations of the usage, go to [Ballerina By Examples](https://ballerina.io/learn/by-example/).
* Chat live with us via our [Discord server](https://discord.gg/ballerinalang).
* Post all technical questions on Stack Overflow with the [#ballerina](https://stackoverflow.com/questions/tagged/ballerina) tag.
