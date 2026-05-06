# Detect and Resend Failed Emails

This example demonstrates how to automatically detect failed or bounced emails in HubSpot CRM and attempt to resend them. The script retrieves all email engagements, checks their status, and creates new email records for any that have failed or bounced.

## Prerequisites

1. **HubSpot Setup**
   > Refer to the [HubSpot setup guide](https://github.com/ballerina-platform/ballerina-library/blob/main/ballerinax/hubspot.crm.engagements.email/Module.md#setup-guide) to obtain OAuth2 credentials.

2. **Configuration**
   Create a `Config.toml` file in the project root directory with your HubSpot OAuth2 credentials:

   ```toml
   clientId = "<Your Client ID>"
   clientSecret = "<Your Client Secret>"
   refreshToken = "<Your Refresh Token>"
   ```

## Run the Example

Execute the following command to run the example. The script will scan all email engagements and resend any that have a `FAILED` or `BOUNCED` status.

```shell
bal run
```