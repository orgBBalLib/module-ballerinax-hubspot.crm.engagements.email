# Detect and Resend Failed Emails

This example demonstrates how to automatically detect failed or bounced emails in HubSpot CRM and resend them. The script retrieves all emails, checks their status, and creates new email records for any that have failed or bounced.

## Prerequisites

1. **HubSpot Setup**
   > Refer to the [HubSpot setup guide](https://github.com/ballerina-platform/ballerina-central-connectors/blob/main/docs/Setup-guide-for-HubSpot-connectors.md) to obtain your OAuth2 credentials.

2. **Configuration**
   
   Create a `Config.toml` file in the project root directory with your HubSpot OAuth2 credentials:

   ```toml
   clientId = "<Your Client ID>"
   clientSecret = "<Your Client Secret>"
   refreshToken = "<Your Refresh Token>"
   ```

## Run the Example

Execute the following command to run the example. The script will print its progress to the console, indicating which emails were resent and which were skipped.

```shell
bal run
```