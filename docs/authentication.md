# Authentication

To get started you'll need an **API Key**.

> **Never share your API Key or expose it publicly!**
>
> Your key should only be used to make requests from server-side environments. You should never use the API Key from a frontend application.

Your api key should be sent with every request as the `x-api-key` header

```
curl --location --request GET 'https://app-api.cinebody.com/app/3.0/organizations' \
--header 'x-api-key: YOUR_API_KEY'
```