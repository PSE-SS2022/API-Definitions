# Events Definitions
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

## Categories
```
SPORTS, FESTIVAL, STUDY, READING, EATING, SOCIAL
```

## Get Planned Events
- path: `/event/planned`
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
        "title": "Event title",
        "duration": 60, // in minutes
        "startDate": 0, // unix time in seconds,
        "visibility": "PUBLIC",
        "numParticipants": 0,
        "maxParticipants": 0,
        "creator": {
          "id": "UUID",
          "displayName": "FirstName LastName#UID"
        }
      },
      ...
    ]
  }
  ```

## Visibility
```
PUBLIC, FRIENDS, PRIVATE
```

## Get Feed for User
- path: `/event/feed`
- Query Params
  - category: String
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
        "title": "Event title",
        "description": "Lorem ipsum dolor sid...",
        "visibility": "PUBLIC",
        "numParticipants": 0,
        "maxParticipants": 0,
        "timeSlots": [
          {
            "startTime": 0, // unix time seconds
            "endTime": 0 // unix time seconds
          }
        ]
        "creator": {
          "id": "UUID",
          "displayName": "FirstName LastName#UID"
        }
      },
      ...
    ]
  }
  ```

## Get Events of Current User
- path: `/user/events`
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
        "title": "Event title",
        "description": "Lorem ipsum dolor sid...",
        "visibility": "PUBLIC",
        "numParticipants": 0,
        "maxParticipants": 0,
        "timeSlots": [
          {
            "startTime": 0, // unix time seconds
            "endTime": 0 // unix time seconds
          }
        ]
        "creator": {
          "id": "UUID",
          "displayName": "FirstName LastName#UID"
        }
      },
      ...
    ]
  }
  ```

## Search for Events
- path: `/event`
- Query Params
  - name: String
  - category: String
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
        "title": "Event title",
        "description": "Lorem ipsum dolor sid...",
        "visibility": "PUBLIC",
        "numParticipants": 0,
        "maxParticipants": 0,
        "timeSlots": [
          {
            "startTime": 0, // unix time seconds
            "endTime": 0 // unix time seconds
          }
        ]
        "creator": {
          "id": "UUID",
          "displayName": "FirstName LastName#UID"
        }
      },
      ...
    ]
  }
  ```

## Report Event
- path: `/event/<id>/report`
  - id: `Event ID`
- Request Body
  ```JSON
  {
    "reason": "Lorem ipsum dolor sid"
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## Get Details of a Event
- path: `/event/<id>`
  - id: `Event id`
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {
    "id": "UUID",
    "title": "Event title",
    "description": "Lorem ipsum dolor sid...",
    "visibility": "PUBLIC",
    "participants": [
      {
        "id": "UUID",
        "displayName": "see other occurrences"
      }
    ],
    "maxParticipants": 0,
    "timeSlots": [
      {
        "startTime": 0, // unix time seconds
        "endTime": 0 // unix time seconds
      }
    ]
    "creator": {
      "id": "UUID",
      "displayName": "FirstName LastName#UID"
    },
    "algorithm": "SIMPLE",
    "duration": 0,
    "startDate": 0, // unix time seconds, only when already planned
    "questionnaire": [
      {
        "id": 0,
        "question": "Frage?",
        "answers": [
          {
            "id": 0
            "answer": "Antwort",
            "users": [ // only when already planned, role > MEMBER
              {
                "id": "UUID",
              }
            ]
          }
        ]
      }
    ]
  }
  ```

## Sign up for a Event
- path: `/event/<id>/signup/`
  - id: `Event ID`
- Request Body
  ```JSON
  {
    "to": "UUID", // Event UUID
    "timeSlots": [
      {
        "startTime": 0, // unix time seconds
        "endTime": 0 // unix time seconds
      }
    ],
    // Multiple questions, 1 Answer per Question
    "questionnaire": { // Map Question: Answer
      "0": 0,
      "1": 2,
      ...
    }
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## Sign out of a Event
- path: `/event/<id>/signout`
  - id: `Event ID`
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {}
  ```

## Create Event
- path: `/event`
- method: POST
- Request Body
  ```JSON
  {
    "title": "Title", 
    "timeSlots": [
      {
        "startTime": 0, // unix time seconds
        "endTime": 0 // unix time seconds
      }
    ], 
    "duration": 0, // in minutes
    "visibility": "PUBLIC", 
    "algorithm": "SIMPLE",
    "deadline": 0, // unix time seconds
    "description": "Lorem ipsum dolor sid...", // optional
    "maxNumParticipants": 0, // optional
    "category": "SEE_ABOVE", // optional
    "questionnaire": [ // optional
      {
        "question": "Who you gonna call?",
        "answers": [
          "Ghostbusters",
          "Talip",
          "Abdullah"
        ]
      }
    ]
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## Edit Event
- path: `/event/<id>`
  - id: `Event ID`
- method: PUT
- Request Body
  ```JSON
  { // Sent the ones you want to update
    "id": "UUID",
    "title": "Title", 
    "visibility": "PUBLIC", 
    "description": "Lorem ipsum dolor sid...", // optional
    "maxNumParticipants": 0, // optional
  }
  ```
- Response Body
  ```JSON
  {
    "See detail"...
  }
  ```

## Delete Event
- path: `/event/<id>`
  - id: `Event ID`
- method: DELETE
- Request Body
  ```JSON
  {}
  ```
- Response Body
  ```JSON
  {}
  ```

## Set Events as synched
- path: `/event/synced/`
- Request Body
  ```JSON
  [
    "UUID",
    "UUID",
    "UUID",
    ...
  ]
  ```
- Response Body
  ```JSON
  {}
  ```

## Change User Role in Event
- path: `/event/role`
- Request Body
  ```JSON
  {
    "id": "UUID",
    "userID": "UUID",
    "role": "HELPER"
  }
  ```
- Response Body
  ```JSON
  {}
  ```

## EventRole
```
OWNER, ORGANIZER, HELPER, ATTENDANT
```
