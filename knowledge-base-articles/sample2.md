# Sample 2

## "Invalid policy configuration" error is returned when trying to delete users via dataflow jobs.

### Symptom
Users cannot be deleted in bulk by using a dataflow because the job fails with `"Invalid policy configuration"` error.

### Environment
- SAP Customer Data Cloud
- Dataflows (IdentitySync)
- Policies

### Cause
The automated email policy "sendAccountDeletedEmail" is enabled on the API key. This policy must be disabled prior to performing bulk actions using a dataflow to avoid unintentionally sending spam emails.

### Resolution
As a workaround, create a new API key and add it as a child of the existing API key. These two API keys form a site group. The existing API key will be considered the parent and has the "sendAccountDeletedEmail" policy enabled. In the new child API key, override the parent API key's "sendAccountDeletedEmail" policy and create a dataflow to delete user accounts without sending automated emails (see Scenario 2 below).

For clarity, take the following scenarios:
- Scenario 1 - parent site:
  1. Go to Identity >> Security >> Identity Verification >> enable "Account delete confirmation" policy in the Admin Console. 
  2. Create a new dataflow with the first step as "datasource.read.gigya.account" (select * from accounts).
  3. Add the second step as datasource.write.gigya.generic (apiMethod=accounts.deleteAccount, apiParams.sourceField=UID, apiParams.paramName=UID).
  4. Execute the dataflow job from this parent site.
     > Result: automated account delete confirmation emails are sent.
- Scenario 2 - child site:
  1. Go to Identity >> Security >> Identity Verification >> enable "Override parent settings" in the Account Verfication section >> disable "Account delete confirmation" policy.
  2. Create a dataflow with the first step as "datasource.read.gigya.account" (select * from accounts).
  3. Add the second step as datasource.write.gigya.generic (apiMethod=accounts.deleteAccount, apiParams.sourceField=UID, apiParams.paramName=UID).
  4. Execute the dataflow job from this child site.
     > Result: automated account delete confirmation emails are not sent.

[(Back to Table of Contents)](../README.md)
