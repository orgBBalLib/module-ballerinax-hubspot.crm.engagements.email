# Detect and Resend Failed Emails

This example demonstrates how to automatically detect failed or bounced emails in HubSpot CRM and resend them. The script retrieves all emails, checks their status, and creates new email engagements to resend any that have failed or bounced.

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

Execute the following command to run the example. The script will check all emails in your HubSpot account, identify any with `FAILED` or `BOUNCED` status, and attempt to resend them.

```shell
bal run
```

The script will print progress messages to the console, indicating which emails were resent and which were skipped.