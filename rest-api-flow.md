```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  Client->>+Server: GET /resource
  Server->>+Database: SELECT * FROM table
  Database-->>-Server: Return Data (JSON)
  Server-->>-Client: 200 OK (JSON)


```

# Rest API Interaction Flow


## 1. Create User

### Request

- Method: `POST`
- Endpoint: `/api/users/create`
- Headers:
    - `Content-Type: application/json`
    - `Accept: application/json`
- Body:
  ```json
  {
    "name": "Foo Bar"
  }
  ```

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "message": "User created successfully"
}

```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/create
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Create User in Database
  Database-->>-Server: User Created
  Server-->>-Client: Return HTTP Response (201 Created)

  note over Client: Response:
  note over Client: HTTP/1.1 201 Created
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

```

---

## 2. Get Sleep Improvements

### Request:

- Method: `GET`
- Endpoint: `/api/sleep/improvements`
- Headers:
    - `Accept: application/json`

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "improvements": [
    {
      "id": "1",
      "description": "I would go to sleep easily"
    },
    {
      "id": "2",
      "description": "I would sleep through the night"
    },
    {
      "id": "3",
      "description": "I'd wake up on time, refreshed"
    }
  ]
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: GET
  note over Client: Endpoint: /api/sleep/improvements
  note over Client: Headers

  Client->>+Server: Send GET Request
  Server->>+Database: Query Improvements
  Database-->>-Server: Return Improvements
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response:
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction


```
---

## 3. Post Sleep Improvement

### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/improvement`
- Parameters:
    - `{userID}`: The ID of the user for whom the improvement is being added
- Headers:
    - `Accept: application/json`
    - `Content-Type: application/json`
- Body:

```json
{
  "improvements": [
    {
      "userID": "31",
      "improvementID": 1
      "improvement": "I would go to sleep easily"
    }
  ]
}
```

### Response:

```http
HTTP/1.1 201 Created
Content-Type: application/json
```

```json
{
  "message": "Improvement added successfully"
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/{userID}/improvement
  note over Client: Parameters
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Add Improvement for User
  Database-->>-Server: Improvement Added
  Server-->>-Client: Return HTTP Response (201 Created)
  
  note over Client: Response:
  note over Client: HTTP/1.1 201 Created
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data
```
## 4. Get Sleep Struggle Durations

### Request:

- Method: `GET`
- Endpoint: `/api/sleep/struggle-durations`
- Headers:
    - `Accept: application/json`

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "durations": [
    {
      "id": "1",
      "duration": "Less than 2 weeks"
    },
    {
      "id": "2",
      "duration": "2 to 8 weeks"
    },
    {
      "id": "3",
      "duration": "More than 8 weeks"
    }
  ]
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: GET
  note over Client: Endpoint: /api/sleep/struggle-durations
  note over Client: Headers

  Client->>+Server: Send GET Request
  Server->>+Database: Query Struggle Durations
  Database-->>-Server: Return Durations
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```

---

## 5. Post Sleep Struggle Suration

### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/struggle/duration`
- Parameters:
    - `{userID}`: The ID of the user for whom the struggle duration is being added
- Headers:
    - `Accept: application/json`
    - `Content-Type: application/json`
- Body:

```json

{
    "userID": "31",
    "durationID": 1
    "duration": "More than 8 weeks"
}

```

### Response:

```http
HTTP/1.1 201 Created
Content-Type: application/json
```

```json
{
  "message": "Struggling duration added successfully"
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/{userID}/struggle/duration
  note over Client: Parameters
  note over Client: Headers

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Add Struggle Duration to User
  Database-->>-Server: Struggle Duration Added
  Server-->>-Client: Return HTTP Response (201 Created)
  
  note over Client: Body: Request JSON Data
  note over Client: Response
  note over Client: HTTP/1.1 201 Created
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```

---
## 6. Set Sleep Time
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/sleep/time`
- Parameters:
    - `{userID}`: The ID of the user for whom the sleep time is being added
- Headers:
    - `Accept: application/json`
    - `Content-Type: application/json`
- Body:

```json
{
  "time": "3:00"
}
```

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "Sleep time added successfully"
}
```

```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/{userID}/sleep/time
  note over Client: Parameters
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Add Sleep Time to User
  Database-->>-Server: Sleep Time Added
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```
---
## 7. Set Wake Up Time
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/wakeup/time`
- Parameters:
    - `{userID}`: The ID of the user for whom the wakeup time is being added
- Headers:
    - `Accept: application/json`
    - `Content-Type: application/json`
- Body:

```json
{
  "time": "10:00"
}
```

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "wakeup time added successfully"
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/{userID}/wakeup/time
  note over Client: Parameters
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Set Wake Up Time for User
  Database-->>-Server: Wake Up Time Set
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```

## 8. Post Sleep Hours
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/sleep/hours`
- Parameters:
    - `{userID}`: The ID of the user for whom the sleep hours is being added
- Headers:
    - `Accept: application/json`
    - `Content-Type: application/json`
- Body:

```json
{
  "hours": 6
}
```

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "sleep hours added successfully"
}
```
```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: POST
  note over Client: Endpoint: /api/users/{userID}/sleep/hours
  note over Client: Parameters
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send POST Request
  Server->>Server: Parse Request Body
  Server->>+Database: Add Sleep Hours to User
  Database-->>-Server: Sleep Hours Added
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```
## 9. Get Sleep Efficiency
### Request:

- Method: `GET`
- Endpoint: `/api/users/{userID}/sleep/efficiency`
- Parameters:
    - `{userID}
- Headers:
    - `Accept: application/json`

### Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "sleepEfficiency": 85
}
```

```mermaid
sequenceDiagram
  participant Client
  participant Server
  participant Database

  note over Client: Method: GET
  note over Client: Endpoint: /api/users/{userID}/sleep/efficiency
  note over Client: Parameters
  note over Client: Headers
  note over Client: Body: Request JSON Data

  Client->>+Server: Send GET Request
  Server->>+Database: Retrieve Sleep Efficiency for User
  Database-->>-Server: Sleep Efficiency Retrieved
  Server-->>-Client: Return HTTP Response (200 OK)
  
  note over Client: Response
  note over Client: HTTP/1.1 200 OK
  note over Client: Content-Type: application/json
  note over Client: Response JSON Data

  note over Server: Handle Database Interaction

```

## Data Modeling

### User Table

| Column                  | Type           | Description                                |
|-------------------------|----------------|--------------------------------------------|
| id                      | integer        | User ID (Primary Key)                      |
| name (required)         | varchar(255)   | User's name (Required)                     |
| efficiency              | integer        | Sleep efficiency                           |
| sleep_hours             | integer        | Number of hours slept                       |
| sleep_time              | time           | Time when user goes to bed                  |
| wakeup_time             | time           | Time when user wakes up                     |
| sleep_improvement  | varchar(255)   | Description of sleep improvement

---

### Sleep Table

| Column                  | Type           | Description                                |
|-------------------------|----------------|--------------------------------------------|
| id                      | integer        | Sleep ID (Primary Key)                     |

---
### Struggle durations Table

| Column                  | Type           | Description                                |
|-------------------------|----------------|--------------------------------------------|
| id                      | integer        | Struggle ID (Primary Key)                  |
| sleep_id (FK)           | integer        | Sleep ID (Foreign Key)                     |
| duration (required)     | varchar(255)   | Duration of sleep struggle (Required)      |

---
### Improvement Table

| Column                  | Type           | Description                                |
|-------------------------|----------------|--------------------------------------------|
| id                      | integer        | Improvement ID (Primary Key)               |
| sleep_id (FK)           | integer        | Sleep ID (Foreign Key)                     |
| user_id (FK)            | integer        | User ID (Foreign Key)                      |
| improvement (required)  | varchar(255)   | Description of sleep improvement (Required)|


```mermaid
erDiagram
    User ||--o{ Improvement : has
    Sleep ||--o{ Improvement : has
    Sleep ||--o{ StruggleDurations : has

    User {
        int id
        string name
        int efficiency
        int sleep_hours
        time sleep_time
        time wakeup_time
        varchar(255) sleep_improvement
    }
    Sleep {
        int id
    }
    StruggleDurations {
        int id
        int sleep_id
        varchar(255) duration
    }
    Improvement {
        int id
        int sleep_id
        int user_id
        varchar(255) improvement
    }


```
