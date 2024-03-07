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

To use the Forum API, you need to create an account and get an API key. You can then use this API key to make requests to our server. Learn more about getting started [here](https://socify.cloud/guides/authentication.md).

## Endpoints

All below endpoints are prefixed with `https://api.socify.cloud`. Authentication, as described above, is required for all endpoints.

### `POST /forum/post/{forum-id}`


### `GET /forum/post/{forum-id}`


### `PUT /forum/post/{forum-id}`


### `DELETE /forum/post/{forum-id}`


### `POST /forum/post/{forum-id}/reaction`


### `DELETE /forum/post/{forum-id}/reaction`


### `POST /forum/post/{forum-id}/comment`


### `PUT /forum/post/{forum-id}/comment`


### `DELETE /forum/post/{forum-id}/comment`


### `GET /forum/list`


### `GET /forum/search`


