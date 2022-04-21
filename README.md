# chat_api_graphql

This is a Python ASGI Implementation with Graphql for message communication

## Test Locally


```
python3 -m venv chat_api_env
source chat_api_env/bin/activate
pip install -r requirements.txt

```

Load server
```
uvicorn app:app --reload
```
## We will build a GraphQL API that allows users to message each other.

The goal is to implement the following:

- A mutation to create a new user. A user will have a user_id and a username.
- A mutation to create a new message. A message will have a sender and a recipient.
- A query to retrieve the user_id of a user given its username.
- A query to list all the messages addressed to a user.
- A subscription that sends new messages to subscribed clients when they are created.


## Test Subscription
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

In the first window, paste the following subscription in the GraphQL editor and hit play:

```
subscription {
  messages(userId: "2") {
    content
    senderId
    recipientId
  }
}
```
In the second window, paste the following subscription in the GraphQL editor and hit play:


```
mutation {
  createMessage(
    senderId: "1",
    recipientId: "2",
    content:"Hello there"
  ) {
    success
    message {
      content
      recipientId
      senderId
    }
  }
}
```

Subscription will listen and flush the data

![Screenshot 2022-04-20 at 9 51 42 PM](https://user-images.githubusercontent.com/335651/164303030-0e96259c-6c64-4064-aaed-2c662a4c3a38.png)


## Deploy on Heroku

Hi Lets deploy
