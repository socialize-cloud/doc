# API Call Authentication

APIs from Socify Cloud usually require authentication to access. This document describes how to authenticate your API calls.

## API Key 

To authenticate your API calls, you need to use an API key. You can get an API key for a specific product you are using, or a global access API key. For example, if you are using the Forum API, you can either use an API key for the Forum API or a global API key. 

> API keys are sensitive information. Do not share your API keys with anyone, nor expose them in public repositories or frontend code.

After obtaining an API key, you can use it in your API calls by providing it in the `Authorization` header. The value of the `Authorization` header should be `Bearer <API-KEY>`. For example:

```http
GET /forum/post HTTP/1.1
Host: api.socify.cloud
Authorization: Bearer <API-KEY>
```
