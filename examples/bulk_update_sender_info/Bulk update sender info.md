# Bulk Update Sender Info

This example demonstrates how to bulk update the sender information for scheduled emails in HubSpot CRM. The script retrieves all emails, filters for those with a "SCHEDULED" status, and updates their sender email address, first name, and last name.

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

Execute the following command to run the example. The script will retrieve all emails, identify those with "SCHEDULED" status, and update their sender information.

```shell
bal run
```

The script will print progress messages to the console indicating which emails were updated and which were skipped.