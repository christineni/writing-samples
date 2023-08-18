# Sample 4
## Google Sign-In returns 400 "DEVELOPER_ERROR" on Android mobile application.

### Symptom
Google Sign-in implemented with the SAP Customer Data Cloud Android SDK returns `400 "DEVELOPER_ERROR"` during login.

### Environment
- SAP Customer Data Cloud
- Android SDK
- Social Login
  
### Resolution
Ensure the following configurations have been implemented correctly:
- In the Google Developers Console, verify you have both a Web OAuth Client ID and an Android OAuth Client ID in the same project.
- Verify the Android Client ID is set up correctly with SHA1 signature and package name.
- Verify the Web Client ID set in the `AndroidManifest.xml` file is the Web Client ID generated when you created your Google project.
  
  > Note: this is also the same Web Client ID as the one set for the Google Consumer Key field on the Providers Configuration page in the Admin Console.

- Ensure all the URLs that participate in the redirect social login flow are added to the Trusted Site URLs list.

[(Back to Table of Contents)](../README.md)
