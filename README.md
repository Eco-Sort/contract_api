* User object
```
{
  id: integer
  username: string
  role : string
  created_at: datetime
  updated_at: datetime
}
```
* garbage object
```
{
  image: string
  classification : <classification object>

  created_at: datetime
  updated_at: datetime
}
```

# Users
## Admin
**GET /users**
----
  Returns all users in the system.
* **URL Params**  
  None
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:**  
* **Code:** 200  
  **Content:**  
```
{
  users: [
           {<user_object>},
           {<user_object>},
           {<user_object>}
         ]
}
```

**GET /users/:id**
----
  Returns the specified user.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:** 
* **Code:** 200  
  **Content:**  `{ <user_object> }` 
* **Error Response:**  
  * **Code:** 404  
  **Content:**
   ```
  {
    status: 404,
    message: "User Doesn't Exist",
  }
  ```
  OR  
  * **Code:** 401  
  **Content:**
  ```
  {
    status: 401,
    message: "Unauthorized",
  }
  ```

**GET /users/:id/images**
----
  Returns all processed garbage images associated with the specified user.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:**  
* **Code:** 200  
  **Content:**  
```
{
  orders: [
           {<order_object>},
           {<order_object>},
           {<order_object>}
         ]
}
```
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "User doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Content:** `{ error : error : "You are unauthorized to make this request." }`

**POST /users**
----
  Creates a new User and returns the new object.
* **URL Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Data Params**  
```
  {
    username: string,
    email: string
  }
```
* **Success Response:**  
* **Code:** 200  
  **Content:**  `{ <user_object> }` 

**PATCH /users/:id**
----
  Updates fields on the specified user and returns the updated object.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
```
  {
  	username: string,
    email: string
  }
```
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:** 
* **Code:** 200  
  **Content:**  `{ <user_object> }`  
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "User doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Content:** `{ error : error : "You are unauthorized to make this request." }`

**DELETE /users/:id**
----
  Deletes the specified user.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:** 
  * **Code:** 204 
* **Error Response:**  
  * **Code:** 404  
  **Content:** `{ error : "User doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Content:** `{ error : error : "You are unauthorized to make this request." }`
