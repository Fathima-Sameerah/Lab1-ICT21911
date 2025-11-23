# Course Service API - Postman Testing Guide

## Base URL
```
http://localhost:8080
```

---

## 1. GET All Courses
**Method:** `GET`  
**URL:** `http://localhost:8080/api/courses`  
**Headers:** None required  
**Body:** None  

**Expected Response (200 OK):**
```json
[]
```
(Empty array initially, will show courses after you create some)

---

## 2. GET Course by ID
**Method:** `GET`  
**URL:** `http://localhost:8080/api/courses/1`  
**Headers:** None required  
**Body:** None  

**Expected Response (200 OK):**
```json
{
    "id": 1,
    "title": "Spring Boot Course"
}
```

**Expected Response (404 Not Found):**
```
(Empty response body)
```

---

## 3. CREATE Course (POST)
**Method:** `POST`  
**URL:** `http://localhost:8080/api/courses`  
**Headers:**
```
Content-Type: application/json
```
**Body (raw JSON):**
```json
{
    "title": "Spring Boot Course"
}
```

**Expected Response (201 Created):**
```json
{
    "id": 1,
    "title": "Spring Boot Course"
}
```

**Example Request Bodies:**
```json
{
    "title": "Java Programming"
}
```

```json
{
    "title": "Web Development"
}
```

```json
{
    "title": "Database Design"
}
```

---

## 4. UPDATE Course (PUT)
**Method:** `PUT`  
**URL:** `http://localhost:8080/api/courses/1`  
**Headers:**
```
Content-Type: application/json
```
**Body (raw JSON):**
```json
{
    "title": "Advanced Spring Boot Course"
}
```

**Expected Response (200 OK):**
```json
{
    "id": 1,
    "title": "Advanced Spring Boot Course"
}
```

**Expected Response (404 Not Found):**
```
(Empty response body)
```

---

## 5. DELETE Course
**Method:** `DELETE`  
**URL:** `http://localhost:8080/api/courses/1`  
**Headers:** None required  
**Body:** None  

**Expected Response (204 No Content):**
```
(Empty response body)
```

**Expected Response (404 Not Found):**
```
(Empty response body)
```

---

## Testing Sequence (Recommended Order)

1. **GET All Courses** - Should return empty array `[]`
2. **POST Create Course** - Create a course with title "Spring Boot Course"
3. **GET All Courses** - Should now show the created course
4. **GET Course by ID** - Get the course with ID 1
5. **PUT Update Course** - Update the course title
6. **GET Course by ID** - Verify the update
7. **DELETE Course** - Delete the course
8. **GET All Courses** - Should return empty array again

---

## Postman Setup Instructions

### For POST and PUT requests:
1. Select the HTTP method (POST or PUT)
2. Click on **Headers** tab
3. Add header:
   - Key: `Content-Type`
   - Value: `application/json`
4. Click on **Body** tab
5. Select **raw** radio button
6. Select **JSON** from the dropdown
7. Paste the JSON body content

### For GET and DELETE requests:
- Just select the method and enter the URL
- No headers or body needed

---

## Example: Complete Postman Collection

### Request 1: Create Course
- Method: `POST`
- URL: `http://localhost:8080/api/courses`
- Headers: `Content-Type: application/json`
- Body:
```json
{
    "title": "Introduction to Java"
}
```

### Request 2: Get All Courses
- Method: `GET`
- URL: `http://localhost:8080/api/courses`

### Request 3: Get Course by ID
- Method: `GET`
- URL: `http://localhost:8080/api/courses/1`

### Request 4: Update Course
- Method: `PUT`
- URL: `http://localhost:8080/api/courses/1`
- Headers: `Content-Type: application/json`
- Body:
```json
{
    "title": "Advanced Java Programming"
}
```

### Request 5: Delete Course
- Method: `DELETE`
- URL: `http://localhost:8080/api/courses/1`

