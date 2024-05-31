
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
* sorting_object
```
{
  sorting_bin: string
  instruction: string
  created_at: datetime
  updated_at: datetime
}
```
* category_object
```
{
  label: string
  sorting : <sorting object>
  created_at: datetime
  updated_at: datetime
}
```
* garbage object
```
{
  image: string
  classification : <category_object>
  created_at: datetime
  updated_at: datetime
}
```
## Auth
**POST /auth/login**
----
  Login for admin and client
  * **Role**  
  None
* **URL Params**  
 None
* **Data Params**  
   ```
  {
    username: string,
    password: string,
  }
  ```
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Content:**
     ```
  {
    status: 200,
    message: "Welcome",
    data: { 
			token :"token string",
			user_id : 123
         }	
  }
  ```
* **Error Response:**  
  * **Code:** 422  
  **Content:**
   ```
  {
    status: 422,
    message: "<Error Message>",
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
  
**POST /auth/register**
----
  Register for client
  * **Role**  
  None
* **URL Params**  
 None
* **Data Params**  
   ```
  {
    username: string,
    password: string,
    re_password: string,
    gender: <0(female) or 1(male) bool>,
  }
  ```
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Content:**
     ```
  {
    status: 200,
    message: "Success",
    data: { 
			user_id : 123
         }
  }
  ```
* **Error Response:**  
  * **Code:** 422  
  **Content:**
   ```
  {
    status: 422,
    message: <Error Message string>,
  }
  ```
 

## Users
**GET /users**
----
  Returns all users in the system.
* **Role**  
  Admin
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
		status: 200,
		message: "Success",
		data: { 
				users :[
			           {<user_object>},
			           {<user_object>},
			           {<user_object>}
			           ]
	         }
	}
```
* **Error Response:**  
  * **Code:** 401  
  **Content:**
  ```
  {
    status: 401,
    message: "Unauthorized",
  }
  ```

**GET /users/:id**
----
  Returns the specified user.
  * **Role**  
  Admin
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
  * **Role**  
  Admin
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
		status: 200,
		message: "Success",
		data: { 
				images :[
			           {<garbage_object>},
			           {<garbage_object>},
			           {<garbage_object>}
			           ]
	         }
	}
	```
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
