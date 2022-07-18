# SNO-APIS

BASE_URL(sandbox) = "http://api.shopoth.net/3ps",
BASE_URL(live) = "https://api.shopoth.com/3ps"
Authentication

* **URL**: `{BASE_URL}/api/v1/login/`

* **Method:** `POST`

*  **Headers:**
	 ``
*  **Request Parameters:**
```
 requires :username, type: String
 requires :password, type: String
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
{
   "success": true,
   "status_code": 200,
   "message": "Successfully logged in.",
   "data": {
       "token": "eyJhbGciOiJIUzI1NiJ9.IiQyYSQxMiRZZFdkOTdUZ0ZXUFBLUUNuUGpvbG9PZnV3dnBhamhZMXQ3VnF4TFNjUUlEZ0ZtM2ZoSEhOZSI.zUWGkcZm-55SrECarrNHH64EApY7Iz3MHyCmHM04X5M",
       "name": "Jon",
       "phone": "01759408190",
        "username": "jon@agami.ltd"
   }
}
 

```


* ** Error Response:**
* **Code:** `403`
  	* **If username or password not matched then:**
  	* **Content:**
```json
{
   "success": false,
   "status_code": 403,
   "message": "Invalid username or password",
   "data": []
}

```

