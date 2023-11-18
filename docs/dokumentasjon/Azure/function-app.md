# Function app
## Authenticating from client
### Keys
If the function app you want to access is using keys as authentication type or "authType": "function", you need to create a host key to be able to access your functions. Navigate to the Function app in the Azure portal, and create a new host key.

![image](https://github.com/vtfk/dev-docs/assets/25528003/8ac5aa9a-e975-45b3-803d-c1d9b675365e)

A host key should only be used ONE single place - for easy rotation management of the key. If you need to access the function from something - create a new key.

To access a function with the key, it is reccommended to pass the key in the header "x-functions-key" (` Headers: { "x-functions-key": <your-key> }`) . If you have to use url query params, you pass it as `?code={key]` in the url.

### Entra ID / Azure AD authentication
If the function app you want to access is using Entra ID as authentication, you need to create or use an app registration to be able to access it.
- First create or find the app registration you want to use to represent you / the client, and give it API permission for the App function you want to access.
![image](https://github.com/vtfk/dev-docs/assets/25528003/0efd7c6e-3fab-4566-9624-de8f9fe072d5)
- If admin consent is required, grant it, or get an admin to grant it.
- Create a new secret or upload a certificate on the app registration you are using as the client.
![image](https://github.com/vtfk/dev-docs/assets/25528003/c72b0460-0426-4718-84cf-fc5c6de4e55f)
- You should now have all you need to get an access token you can use to access the function app [https://learn.microsoft.com/en-us/azure/databricks/dev-tools/service-prin-aad-token](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/service-prin-aad-token)
- TODO: Add examples on how to get the access token
