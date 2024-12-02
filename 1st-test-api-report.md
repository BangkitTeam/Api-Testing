## 1st API Test Report

**Introduction**

This report documents the results of testing the WasteWise API using Postman. The functionalities tested include image upload, waste classification, and recommendations.

**Authentication**

The API uses Bearer token authentication. A sample token is provided:

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwidXNlcm5hbWUiOiJhbGkxMjMiLCJlbWFpbCI6ImFsaUBleGFtcGxlLmNvbSIsImlhdCI6MTczMzEyNDk4NywiZXhwIjoxNzMzMjExMzg3fQ.dDM1veP7sVcS13Cm3ebsa0HdNh9l4b-9PvtTVpXKLdM
```

**API Endpoints**

**1. Image Upload (/upload/upload)**

* **Method:** POST
* **Authentication:** Bearer token
* **Request Body:** Form data with `file` field containing the image file

**Expected response based on the code:**
```json
{
  "message": "File uploaded successfully!",
  "file": {
    "id": 1,
    "userId": 1,
    "image_name": "image_name",
    "image_url": "image_url",
    "type": "image/jpeg",
    "size": 12345,
    "description": null,
    "createdAt": "2023-11-22T12:34:56Z"
  }
}
```

**Response I get:**

```json
{
  "message": "File uploaded successfully!",
  "file": {
    "id": 1,
    "userId": 1,
    "image_name": "image_name",
    "image_url": "image_url",
    "type": "image/jpeg",
    "size": 12345,
    "description": null,
    "createdAt": "2023-11-22T12:34:56Z"
  }
}
```

**Test Results:**

* Image upload was successful. 
* The response contains details about the uploaded file, including id, user ID, image name, URL, type, size, and creation date.

**2. Waste Classification (/prediction/latest-prediction)**

* **Method:** GET
* **Authentication:** None

**Expected response based on the code:**

```json
{
  "id": 1,
  "uploadId": 1,
  "prediction": "prediction_category",
  "confidence": 0.99,
  "userId": 1
}
```

**Response I get:**
```json
{
    "id": 2,
    "uploadId": 2,
    "prediction": "milkbox",
    "confidence": 0.993232011795044,
    "userId": 1
}
```

**Test Results:**

* Fetches the latest prediction, but may not reflect newly uploaded images immediately. (Discussed further in "Recommendations" section)

> udah coba tambah foto baru, pas dicek ulang, latest result nya masih data yang lama

**3. Recommendations**

**a. GET /recommend/recommendations**

* **Method:** GET
* **Authentication:** Bearer token

**Expected response based on the code:**

```json
{
  "userId": 1,
  "prediction_confidence": 0.99,
  "image_url": "image_url",
  "recommendations": [
    {
      "title": "Recommendation 1",
      "description": "Description 1",
      "imageUrl": "image_url"
    },
    // ... more recommendations
  ]
}
```

**Response I get:**
```json
{
    "error": "Failed to get recommendations."
}
```

**Test Results:**

* The initial GET request to `/recommend/recommendations` failed to retrieve recommendations. 

**b. POST /recommend/recommendations**

* **Method:** POST (Raw)
* **Authentication:** Bearer token
* **Request Body:** JSON with `craftIds` array containing recommendation IDs

**Expected response based on the code:**
```json
{
  "message": "Recommendations saved successfully"
}
```

**Response I get:**

```json
{
  "message": "Recommendations saved successfully"
}
```

**Test Results:**

* Sending a POST request with `craftIds` in the body successfully saved recommendations.

**Recommendations Section Issue**

The test results indicate that the `/prediction/latest-prediction` endpoint might not immediately update after a new image upload. This could lead to the `/recommend/recommendations` (GET) endpoint using outdated information for the latest prediction.

**Suggestions:**

* Investigate how the latest prediction is cached and implement a mechanism to refresh the cache upon new image uploads.
* Consider returning an error message or a flag in the `/recommend/recommendations` (GET) response if the prediction used for recommendations is not based on the latest upload.

**Overall**

The API functionalities tested seem to work as expected, with the exception of the potential caching issue in the recommendations section. This report provides a basic overview of the API functionalities and the results of the testing process. 

##### Supporting Evidence
https://drive.google.com/drive/folders/1OEpVnxSMFLPB41kiRDvh2NuDngTT_gxN?usp=sharing
