# Sample 5

## Unable to merge an account with site-identity to an account with OIDC or SAML provider identity.

### Symptom
When a user registers a new account using the same email as an existing account that has a federated identity (SAML or OIDC), the account linking screen does not display the option to merge with the federated identity account.

### Environment
- SAP Customer Data Cloud
- Web SDK
- Customer Identity
- SAML
- OpenID Connect (OIDC)

### Reproducing the Issue
1. Register an account using the federated identity provider option.
2. Logout of the account.
3. Register a new user account using the same email address from step 1 with the site or social login option.
   > Result: the account linking screen is displayed, but there is no option to merge the new account with the federated identity account that has the same email from step 1, so the flow cannot be completed.

### Cause
By default, account linking for federated identities is disabled in the API key policy settings.

### Resolution
Enable account linking for federated identities by calling the [accounts.setPolicies](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4139d66d70b21014bbc5a10ce4041860.html) REST API and pass the parameter `{"federation"={"allowMultipleIdentities":true}}`.

[(Back to Table of Contents)](../README.md)
