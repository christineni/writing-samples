# Sample 1

## Is it possible to include the 'id_token' field in the accounts.login response when using screen-sets?

### Symptom
When using the screen-set feature, accounts.login does not return the `id_token` field in the response.

### Environment
- SAP Customer Data Cloud
- Web SDK 
- Customer Identity

### Resolution
To return the `id_token` field in the accounts.login response, follow these steps:
1. Select Web SDK Configuration on the left-hand menu in the Admin Console.
2. Add `include: "id_token"` to the Web SDK Configuration.
   
   > The possible values for `include` are:
   >  - identities-active
   >  - identities-all
   >  - loginIDs
   >  - emails
   >  - profile
   >  - data
   >  - isLockedOut
   >  - missing-required-fields
   >  - preferences
   >  - subscriptions
   >  - groups
   >  - id_token

[(Back to Table of Contents)](../README.md)
