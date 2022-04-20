# chat_api_graphql


## We will build a GraphQL API that allows users to message each other. 

The goal is to implement the following:

A mutation to create a new user. A user will have a user_id and a username.
A mutation to create a new message. A message will have a sender and a recipient.
A query to retrieve the user_id of a user given its username.
A query to list all the messages addressed to a user.
A subscription that sends new messages to subscribed clients when they are created.


# Test Subscription
Let’s begin by creating two users, user_one and user_two. Paste the following mutation and hit play.

```
mutation {
  createUser(username:"user_one") {
    success
    user {
      userId
      username
    }
  }
}
```
```
mutation {
  createUser(username:"user_two") {
    success
    user {
      userId
      username
    }
  }
}
```
Now we have 2 users created , If you looked at the responses from the createUser mutations you already know what IDs were assigned to them, but let’s assume we only know the usernames, so we will use the userId query to retrieve the IDs.

```
query {
  userId(username:"user_one")
}
```
