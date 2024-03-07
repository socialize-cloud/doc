# Socify Cloud Forum API

The Forum API from Socify Cloud allows you to create a forum for your users to discuss topics. Users can react and comments to other people's posts and comments. This document is the detailed specification of the API usage. Learn more about this product [here](https://socify.cloud/products/forum).

## Defining Terminoogies

| Term | Definition |
| ---- | ---------- |
| Forum | A forum is a place where users can discuss topics. Users can create posts and comments. |
| Forum Post | A post is an item in the forum a user creates. Other users can react and comment on the post. |
| Comment | A comment is a response to a post or another comment. Users can react and reply to comments. |
| Reaction | A reaction is a response to a post or comment. Users can react with emojis, upvotes, or downvotes; how they react can be managed by you. |
| Topic Tag | A topic tag is a label associated with each forum post. You can define the structure of the forum by defining categories using tags. |

## Authentication

To use the Forum API, you need to create an account and get an API key. You can then use this API key to make requests to our server. Detailed descriptions on how to perform authentication in API calls can be found [here](../guides/authentication.md).

## User ID

In the API, you will need to provide the `userId` of the user who is creating the post, comment, or reaction. This `userId` is the unique identifier of the user in your system. You can learn more about how to manage user IDs in our [guide](../guides/user-id.md).

## Endpoints

All below endpoints are prefixed with `https://api.socify.cloud`. Authentication, as described above, is required for all endpoints.

### Creating a Post 

`POST /forum/post`

This endpoint is used to create a new forum post in the forum. After requesting, the server will create the post and return the post information.

Example Request:

```json
{
    "userId": "user-id",
    "title": "My First Post",
    "content": "This is the content of my first post.",
    "tags": ["tag1", "tag2"]
}
```

Example Response:

```json
{
    "id": "post-id",
    "userId": "user-id",
    "title": "My First Post",
    "content": "This is the content of my first post.",
    "tags": ["tag1", "tag2"],
    "createdAt": "2021-01-01T00:00:00Z",
    "updatedAt": "2021-01-01T00:00:00Z"
}
```

### `GET /forum/post/{forum-id}`

This endpoint is used to get a specific forum post by its ID.

Example Response:

```json
{
    "id": "post-id",
    "userId": "user-id",
    "title": "My First Post",
    "content": "This is the content of my first post.",
    "tags": ["tag1", "tag2"],
    "createdAt": "2021-01-01T00:00:00Z",
    "updatedAt": "2021-01-01T00:00:00Z"
}
```

### `PUT /forum/post/{forum-id}`

This endpoint is used to update a specific forum post by its ID. Whether the user can update a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you. 

### `GET /forum/post/{forum-id}/history`

This endpoint is used to update a specific forum post by its ID. Whether the user can update a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you. 

### `DELETE /forum/post/{forum-id}`

This endpoint is used to delete a specific forum post by its ID. Whether the user can delete a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you, even after deletion (for the period of time you specify).

### `POST /forum/post/{forum-id}/reaction`

This endpoint is used to create a reaction to a specific forum post by its ID. Users can react with emojis, upvotes, or downvotes; how they react (the options for reactions) can be managed by you. Adding a reaction to a post would delete the previous reaction of the user.

### `DELETE /forum/post/{forum-id}/reaction`

This endpoint is used to delete a reaction to a post by its ID. Users can react with emojis, upvotes, or downvotes; how they react (the options for reactions) can be managed by you.

### `POST /forum/post/{forum-id}/comment`


### `PUT /forum/post/{forum-id}/comment`


### `DELETE /forum/post/{forum-id}/comment`


### `GET /forum/list`


### `GET /forum/search`


