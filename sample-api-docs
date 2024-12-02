
# Dicoding Story API Documentation

## Introduction

The **Dicoding Story API** allows users to share stories about Dicoding, similar to Instagram posts but specifically tailored for the Dicoding community.

## Base URL
```
https://story-api.dicoding.dev/v1
```

---

## Table of Contents

1. [Register](#register)
2. [Login](#login)
3. [Add New Story](#add-new-story)
4. [Add Story with Guest Account](#add-story-with-guest-account)
5. [Get All Stories](#get-all-stories)
6. [Detail Story](#detail-story)

---

## 1. Register

### Endpoint
```
POST /register
```

### Request Body
| Field       | Type   | Description                          |
|-------------|--------|--------------------------------------|
| `name`      | string | User's full name                    |
| `email`     | string | Must be unique                      |
| `password`  | string | Must be at least 8 characters long  |

### Response
#### Success
```json
{
  "error": false,
  "message": "User Created"
}
```

---

## 2. Login

### Endpoint
```
POST /login
```

### Request Body
| Field       | Type   | Description                  |
|-------------|--------|------------------------------|
| `email`     | string | User's registered email      |
| `password`  | string | User's password              |

### Response
#### Success
```json
{
  "error": false,
  "message": "success",
  "loginResult": {
    "userId": "user-yj5pc_LARC_AgK61",
    "name": "Arif Faizin",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiJ1c2VyLXlqNXBjX0xBUkNfQWdLNjEiLCJpYXQiOjE2NDE3OTk5NDl9.flEMaQ7zsdYkxuyGbiXjEDXO8kuDTcI__3UjCwt6R_I"
  }
}
```

---

## 3. Add New Story

### Endpoint
```
POST /stories
```

### Headers
| Key           | Value                          |
|---------------|--------------------------------|
| `Content-Type`| `multipart/form-data`          |
| `Authorization` | `Bearer <token>`             |

### Request Body
| Field         | Type     | Description                                     |
|---------------|----------|-------------------------------------------------|
| `description` | string   | Description of the story                       |
| `photo`       | file     | Must be a valid image file, max size 1MB       |
| `lat`         | float    | (Optional) Latitude coordinate                 |
| `lon`         | float    | (Optional) Longitude coordinate                |

### Response
#### Success
```json
{
  "error": false,
  "message": "success"
}
```

---

## 4. Add Story with Guest Account

### Endpoint
```
POST /stories/guest
```

### Request Body
| Field         | Type     | Description                                     |
|---------------|----------|-------------------------------------------------|
| `description` | string   | Description of the story                       |
| `photo`       | file     | Must be a valid image file, max size 1MB       |
| `lat`         | float    | (Optional) Latitude coordinate                 |
| `lon`         | float    | (Optional) Longitude coordinate                |

### Response
#### Success
```json
{
  "error": false,
  "message": "success"
}
```

---

## 5. Get All Stories

### Endpoint
```
GET /stories
```

### Headers
| Key           | Value                          |
|---------------|--------------------------------|
| `Authorization` | `Bearer <token>`             |

### Query Parameters
| Parameter     | Type   | Default | Description                                  |
|---------------|--------|---------|----------------------------------------------|
| `page`        | int    | -       | Page number for pagination                  |
| `size`        | int    | -       | Number of stories per page                  |
| `location`    | int    | 0       | `1` to include only stories with location   |

### Response
#### Success
```json
{
  "error": false,
  "message": "Stories fetched successfully",
  "listStory": [
    {
      "id": "story-FvU4u0Vp2S3PMsFg",
      "name": "Dimas",
      "description": "Lorem Ipsum",
      "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png",
      "createdAt": "2022-01-08T06:34:18.598Z",
      "lat": -10.212,
      "lon": -16.002
    }
  ]
}
```

---

## 6. Detail Story

### Endpoint
```
GET /stories/:id
```

### Headers
| Key           | Value                          |
|---------------|--------------------------------|
| `Authorization` | `Bearer <token>`             |

### Response
#### Success
```json
{
  "error": false,
  "message": "Story fetched successfully",
  "story": {
    "id": "story-FvU4u0Vp2S3PMsFg",
    "name": "Dimas",
    "description": "Lorem Ipsum",
    "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png",
    "createdAt": "2022-01-08T06:34:18.598Z",
    "lat": -10.212,
    "lon": -16.002
  }
}
```

---

## Notes

1. All API responses are in JSON format.
2. Ensure the `Authorization` header includes the Bearer token where required.
3. For `photo` in POST requests, use a valid image file (e.g., `.jpg`, `.png`).

---

This documentation is structured for clarity and ease of use, with all endpoints detailed in one file.

### Reference
1. [Dicoding Story API](https://story-api.dicoding.dev/v1#/)
2. Explained by Chat GPT
