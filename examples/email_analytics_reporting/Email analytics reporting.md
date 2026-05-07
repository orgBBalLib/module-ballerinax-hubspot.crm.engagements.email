# Email Analytics Reporting

This example demonstrates how to fetch email engagement data from HubSpot CRM and generate an analytics summary report. The script retrieves all email engagements, categorizes them by status (sent, bounced, failed, scheduled), and prints a consolidated report to the console.

## Prerequisites

1. **HubSpot Setup**
   > Refer to the [HubSpot setup guide](https://github.com/ballerina-platform/module-ballerinax-hubspot.crm.engagements.email/tree/main/ballerina/Package.md) to obtain your OAuth2 credentials.

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
Total Emails Sent    : 150
Total Emails Bounced : 12
Total Emails Failed  : 5
Total Emails Scheduled    : 23
```