# Socify Cloud Post API

The Post API from Socify Cloud allows you to create a forum or a posting system for your users to discuss any topic. Users can react and comments to other people's posts and comments. This document is the detailed specification of the API usage. Learn more about this product [here](https://socify.cloud/products/post).

## Defining Terminoogies

| Term | Definition |
| ---- | ---------- |
| Post | A post is an item that holds the content a user creates. Other users can react and comment on the post. |
| Comment | A comment is a response to a post or another comment. Users can react and reply to comments. |
| Reaction | A reaction is a response to a post or comment. Users can react with emojis, upvotes, or downvotes; how they react can be managed by you. |
| Topic Tag | A topic tag is a label associated with each post. You can define the structure of a forum or filter posts by defining categories using tags. |
| Series | A series refers to a post's history. When first created, the post will have the same `seriesId` as its `_id`. When edited, the post will have the same `seriesId`, but the `_id` will change. |

## Authentication

To use the Post API, you need to create an account and get an API key. You can then use this API key to make requests to our server. Detailed descriptions on how to perform authentication in API calls can be found [here](../spec/authentication.md).

## User ID

In the API, you will need to provide the `userId` of the user who is creating the post, comment, or reaction. This `userId` is the unique identifier of the user in your system. You can learn more about how to manage user IDs in our [guide](../spec/user-id.md).

## Endpoints

All below endpoints are prefixed with `https://api.socify.cloud`. Authentication, as described above, is required for all endpoints.

### Creating a Post 

Endpoint: `POST /post`

This endpoint is used to create a new post. After requesting, the server will create the post and return the post information.

Example Request:

```json
{
    "post": {
        "userId": "user-id",
        "title": "My First Post",
        "content": "This is the content of my first post.",
        "tags": ["tag1", "tag2"]
    }
}
```

Example Response:

```json
{
    "post": {
        "id": "post-id",
        "userId": "user-id",
        "title": "My First Post",
        "content": "This is the content of my first post.",
        "tags": ["tag1", "tag2"],
        "createdTime": "2021-01-01T00:00:00Z"
    }
}
```

### Getting a Post

Endpoint: `GET /post/{_id}`

This endpoint is used to get a specific post by its ID. Note that this endpoint returns the newest version of the post, whose `seriesId` equals the `_id` you provide, while its `_id` might be different. 

Example Response:

```json
{
    "post": {
        "id": "post-id",
        "userId": "user-id",
        "title": "My First Post",
        "content": "This is the content of my first post.",
        "tags": ["tag1", "tag2"],
        "createdTime": "2021-01-01T00:00:00Z"
    }
}
```

### Editing a Post

Endpoint: `PUT /post`

This endpoint is used to update a specific post by its ID. Whether the user can update a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you. 

In the request body, you can provide the fields you want to update. You do not have to provide all fields, and only the provided fields will be updated. Note that, although not recommended, you can also update the `userId` of the post, meaning that the ownsership of the post can be transferred. In addition, the `_id` field is only used to select which post to edit.

Example Request:

```json
{
    "post": {
        "_id" : "post-id",
        "userId": "user-id", 
        "title": "My Updated Post",
        "content": "This is the updated content of my first post.",
        "tags": ["tag1", "tag2", "tag3"]
    }
}
```

Example Response:

```json
{
    "post": {
        "id": "post-id",
        "userId": "user-id",
        "title": "My Updated Post",
        "content": "This is the updated content of my first post.",
        "tags": ["tag1", "tag2", "tag3"],
        "createdTime": "2021-01-01T00:00:00Z",
    }
}
```

### Getting Post History

Endpoint: `GET /forum/post/{forum-id}/history`

This endpoint is used to update a specific forum post by its ID. Whether the user can update a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you. 

### Deleting a Post

Endpoint: `DELETE /forum/post/{forum-id}`

This endpoint is used to delete a specific forum post by its ID. Whether the user can delete a post can be managed by you. The history of the post can be both accessed through the history endpoint, or viewed in Socify's cloud console by you, even after deletion (for the period of time you specify).

Example Response: 

```json
{
    "success": true
}
```

### Reacting to a Post and Its Comments

Endpoint: `POST /forum/post/{forum-id}/reaction`

This endpoint is used to create a reaction to a specific forum post, or its comments, by its ID. Users can react with emojis, upvotes, or downvotes; how they react (the options for reactions) can be managed by you. Adding a reaction to a post would delete the previous reaction of the user.

### Deleting a Reaction

Endpoint: `DELETE /forum/post/{forum-id}/reaction`

This endpoint is used to delete a reaction to a post by its ID. Users can react with emojis, upvotes, or downvotes; how they react (the options for reactions) can be managed by you.

### Commenting on a Post

Endpoint: `POST /forum/post/{forum-id}/comment`


### Editing a Comment

Endpoint: `PUT /forum/post/{forum-id}/comment`


### Deleting a Comment

Endpoint: `DELETE /forum/post/{forum-id}/comment`


### Listing Posts with Criteria

Endpoint: `GET /forum/list`


### Searching Posts

Endpoint: `GET /forum/search`


