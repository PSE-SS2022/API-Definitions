
# User Definitions
- Request Header
  ```
  Authorization: Bearer <jwt-token>
  ```

## Error
```JSON
{
  "message": "String"
}
```
## SignUp
- path: `/user/signup`
- Request Body
  ```JSON
  {
    "id": "UUID",
    "firstName": "Name",
    "lastName": "LastName",
    "email": "email@test.de"
  }
  ```
- Response Body
  ```JSON
    {}
  ```

## Send FCM Token
- path: `/user/fcmToken`
- Request Body
  ```JSON
  {
    "token": "fcm_token"
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## Search User
- path: `/user`
- Query Params
  - name: String
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {
    [
      {
        "id": "UUID",
        "displayName": "FirstName LastName#UID",
        "relation": "FRIENDS",
        "profilePicture": "URL"
      },
      ...
    ]
  }
  ```
### Relations
```
FRIENDS, BLOCKED, NOT_FRIENDS, FRIEND_REQUEST_SENT, FRIEND_REQUEST_RECEIVED
```

## Get List of Friends/Blocked from Current User
- path: `/userRelations`
- Request Body
  ```JSON
  {}
  ```
- Response Body
    ```JSON
  {
    [
      {
        "id": "UUID",
        "displayName": "FirstName LastName#UID",
        "relation": "FRIENDS",
        "profilePicture": "URL"
      },
      ...
    ]
  }
  ```

## Friend Requests

### Send
- path: `/userRelations/sendFriendRequest`
- method: `POST`
- Request Body
  ```JSON
  {
    "to": "UUID"
  }
  ```
- Response Body
  ```JSON
  {}
  ```

### Get
- path: `/userRelations/friendRequests`
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {
    [
      {
        "id": "UUID",
        "user": {
          "id": "UUID",
          "displayName": "FirstName LastName#UID"
        }
      },
      ...
    ]
  }
  ```

### Accept/Decline
- path: `/userRelations/friendRequests/<id>`
  - id: `FriendRequest ID`
- method: `POST`
- Request Body
  ```JSON
  {
    "answer": true | false
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## Block User
- path: `/userRelations/<id>/block`
  - id: `User ID`
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {}
  ```

## Report User
- path: `/userRelations/<id>/report`
  - id: `User UUID`
- Request Body
  ```JSON
  {
    "reason": "Lorem ipsum dolor me sid...."
  }
  ```
- Response Body
  ```JSON
  {}
  ```
