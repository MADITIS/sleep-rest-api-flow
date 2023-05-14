# REST API Interaction Flow

## 1. Start the App and Enter Name:

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

---

## 2. Get Sleep improvements

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
---

## 3. Post Sleep improvement

### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/improvement`
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

## 4. Get Sleep struggle durations

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

---

## 5. Post sleep struggle duration

### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/struggle/duration`
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
---
## 6. Set sleep time
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/sleep/time`
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
---
## 7. Set wake up time
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/wakeup/time`
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
## 8. Post sleep hours
### Request:

- Method: `POST`
- Endpoint: `/api/users/{userID}/sleep/hours`
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
## 9. Get Sleep Efficiency
### Request:

- Method: `GET`
- Endpoint: `/api/users/{userID}/sleep/efficiency`
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
