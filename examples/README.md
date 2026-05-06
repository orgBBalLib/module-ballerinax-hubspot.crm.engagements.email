# Examples

The `hubspot.crm.engagements.email` connector provides practical examples illustrating usage in various scenarios. Explore these [examples](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples), covering use cases like bulk update sender info, detect resend failed emails, and email analytics reporting.

1. [Bulk update sender info](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/bulk_update_sender_info) - Update sender information across multiple email engagements in bulk.

2. [Detect resend failed emails](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/detect_resend_failed_emails) - Identify failed email engagements and automatically resend them.

3. [Email analytics reporting](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/examples/email_analytics_reporting) - Generate analytics reports based on email engagement data.

## Prerequisites

1. Generate HubSpot credentials to authenticate the connector as described in the [Setup guide](https://central.ballerina.io/ballerinax/hubspot.crm.engagements.email/latest#setup-guide).

2. For each example, create a `Config.toml` file the related configuration. Here's an example of how your `Config.toml` file should look:

    ```toml
    token = "<Access Token>"
    ```

## Running an Example

Execute the following commands to build an example from the source:

* To build an example:

    ```bash
    bal build
    ```

* To run an example:

    ```bash
    bal run
    ```