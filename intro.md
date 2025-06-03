# BASICS
## API
**Application Programming Interface** <br>
API is a set of rules that allow 2 softwares to communicate with each other. 
- it is like a restaurant where the menu is the api and the dishes in the menu are like the functions and methods we choose. The kitchen is the backend that serves the dishes (sends the response)
## REST API 
**Representational State Transfer**<br>
- It is a type of API that works on a specific set of rules and communicates via HTTP requests only through JSON data format.

| HTTP Method | Purpose         | Example      |
| ----------- | --------------- | ------------ |
| GET         | Read data       | `/users`     |
| POST        | Create new data | `/users`     |
| PUT         | Update data     | `/users/123` |
| DELETE      | Delete data     | `/users/123` |

All REST API's are API's but all API's are not REST API's
| Feature       | API (general)               | REST API                                   |
| ------------- | --------------------------- | ------------------------------------------ |
| Definition    | Interface for communication | Specific type of API that uses REST rules  |
| Protocols     | Any (HTTP, WebSocket, etc.) | Always uses HTTP                           |
| Data Formats  | Any (XML, JSON, etc.)       | Usually JSON                               |
| Methods       | Custom or any               | Follows standard HTTP methods (GET, POST…) |
| Stateless     | Not always                  | Always stateless                           |
| URL structure | Not always resource-based   | Always resource-based (`/users/1`)         |

## JSON 
**Javascript Object Notation**<br>
JSON is a data format or the language of the data. It is how data communicates with the client side (frontend) and the server side (backend).
```
{
  "name": "Twinkle",
  "age": 20,
  "isStudent": true,
  "skills": ["Java", "Spring Boot", "React"]
}

```
This is how a JSON looks like (similar to JS objects). It has key-value pairs where the keys are strings. It is inside {} for objects or [] for array.<br><br>
Why is JSON important for REST APIs?<br>
Because REST APIs use HTTP to send and receive data, and the most common format for that data is JSON.<br>
example :
- frontend sends JSON to backend : 
```
{
  "username" : "Twinkle"
  "password" : "xyz"
}
```
- backend processes and responds with JSON :
```
{
  "status" : "success"
  "message" : "login successful"
}
```

## spring boot 
```
Frontend (HTML/React/Android) 
    ↓ HTTP request (GET, POST, etc.)
Spring Boot Backend (REST API) 
    ↓ Java logic (Controller → Service → Database)
Response → Sent back as JSON
```
Spring Boot is a way to create REST APIs which is a way to write backend code, and connect it with the frontend using HTTP requests.<br>
Q. What is the Connection between Spring Boot and REST API? <br>
 - Spring Boot is used to build REST APIs easily.

