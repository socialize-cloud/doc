# Managing User IDs

In many cases, you will need to provide the `userId` of the user who is performing the action in the API. This `userId` is the unique identifier of the user in your system. 

## Examples where `userId` is required

- Creating a post in the Forum API
- Creating a comment in the Forum API
- Creating a reaction in the Forum API

## Best Practices

### Use a unique identifier

The `userId` should be a unique identifier of the user in your system. This identifier should not change over time, and it should be unique across all users in your system.

### Do not expose sensitive information

The `userId` should not expose any sensitive information about the user. For example, you should not use the user's email address or phone number as the `userId`.

### Keep the `userId` consistent

The `userId` should be consistent across all APIs in your system. For example, if you are using the Forum API and the Messaging API, the `userId` should be the same in both APIs.

### Use a UUID

We recommend using an UUID (Universally Unique Identifier) is a good choice for the `userId`. It is a 128-bit number that is unique across all users in your system. You can generate a UUID using libraries available in most programming languages.

