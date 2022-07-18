# SNO-APIS

BASE_URL(sandbox) = "http://api.shopoth.net/3ps",
BASE_URL(live) = "https://api.shopoth.com/3ps"


Authentication API

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
       "token": "eyJhbGciOiJIUzI1NiJ9.IiQyYSQxMiRZZFdkOTdUZ0ZXUFBLUUNuUGpvbG9PZnV3dnBhamhZMXQ3VnF4TFNjUUlEZ0ZtM2ZoSEhOZSI.zUWGkcZm-55SrECarrNHH64EApY7Iz3MHyCmHM04X5M"
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

Customer Order Pack API

* **URL**: `{BASE_URL}/api/v1/customer_orders/{order_id}/pack`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
{
	"packed_items": [
		{
			"line_item_id": 173651, 
			"qr_codes": [PA-115-E710-Uii-006203, PA-115-E710-Uii-006202],
			"location_id": 100
		}
	]
}
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully packed",
   "status_code": 200
}
```

* ** Error Response:*
* **Code:** '402'
  	* **If pay_type of an order is online but not paid:**
  	* **Content:**
```json
{  "success" : false
   "message": "Only successful online payment should pack",
   "status_code": 402
}
```

* ** Error Response:*
* **Code:** '404'
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```

* ** Error Response:*
* **Code:** '406'
  	* **If order item not available in stock:**
  	* **Content:**
```json
{  "success" : false
   "message": "Unable to pack due to unavailable quantity.",
   "status_code": 406
}
```

* ** Error Response:*
* **Code:** '400'
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "line_item_id missing",
   "status_code": 400
}
```
Customer Order send_to_dh API

* **URL**: `{BASE_URL}/api/v1/customer_orders/{order_id}/send_to_dh`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
 requires :sno_chalan_id, type: Integer
 requires :order_ids, type: Array
 requires :distributor_id, type: Integer
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully sent",
   "status_code": 200
}
```

* ** Error Response:*
* **Code:** '404'
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```

* ** Error Response:*
* **Code:** '404'
  	* **If Distributor not found:**
  	* **Content:**
```json
{  "success" : false
   "message": "Distributor not found",
   "status_code": 404
}
```

* ** Error Response:*
* **Code:** '400'
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "sno_chalan_id missing",
   "status_code": 400
}
```

Chalan send_to_fc API

* **URL**: `{BASE_URL}/api/v1/return_chalans/send_to_fc`

* **Method:** `POST`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
 requires :sno_return_chalan_id, type: Integer
 optional :returned_order_ids, type: Array
 optional :cancelled_order_ids, type: Array
 requires :distributor_id, type: String
    
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully sent",
   "status_code": 200
}
```
* ** Error Response:*
* **Code:** '400'
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "Either returned_order_ids or cancelled_order_ids required for making the return chalan",
   "status_code": 400
}
```

* ** Error Response:*
* **Code:** '404'
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```

* ** Error Response:*
* **Code:** '404'
  	* **If Distributor not found:**
  	* **Content:**
```json
{  "success" : false
   "message": "Distributor not found",
   "status_code": 404
}
```

* ** Error Response:*
* **Code:** '400'
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "sno_return_chalan_id missing",
   "status_code": 400
}
```
