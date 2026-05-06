# Email Analytics Reporting

This example demonstrates how to generate an analytics report for email engagements in HubSpot CRM. The script fetches all email engagement records, analyzes their statuses, and produces a summary report showing counts of sent, bounced, failed, and scheduled emails.

## Prerequisites

1. **HubSpot Setup**
   > Refer to the [HubSpot setup guide](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/docs/setup/setup.md) to obtain your OAuth2 credentials.

2. **Configuration**
   
   Create a `Config.toml` file in the project root directory with your HubSpot OAuth2 credentials:

   ```toml
   clientId = "<Your Client ID>"
   clientSecret = "<Your Client Secret>"
   refreshToken = "<Your Refresh Token>"
   ```

## Run the Example

Execute the following command to run the example. The script will fetch email engagements from HubSpot and print an analytics summary to the console.

```shell
bal run
```

Upon successful execution, you will see output similar to:

```
===== Email Engagements Report =====
Total Emails Sent    : 45
Total Emails Bounced : 3
Total Emails Failed  : 1
Total Emails Scheduled    : 12
```