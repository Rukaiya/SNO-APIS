# SNO-APIS

BASE_URL(sandbox) = "Please request for base url when you need",
BASE_URL(live) = "Please request for base url when you need"


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


* **Error Response:**
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
			"location_code": "JR-01-A-A-101"
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

* **Error Response:**
* **Code:**  `402`
  	* **If pay_type of an order is online but not paid:**
  	* **Content:**
```json
{  "success" : false
   "message": "Only successful online payment should pack",
   "status_code": 402
}
```

* **Error Response:**
* **Code:** `404`
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```
* **Error Response:**
* **Code:** `404`
  	* **If order item not found:**
  	* **Content:**
```json
{  "success" : false
   "message": "Item not found.",
   "status_code": 404
}
```

* **Error Response:**
* **Code:** `406`
  	* **If order item not available in stock:**
  	* **Content:**
```json
{  "success" : false
   "message": "Unable to pack due to unavailable quantity.",
   "status_code": 406
}
```

* **Error Response:**
* **Code:** `400`
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "{required_field} missing",
   "status_code": 400
}
```
Customer Order received_form_fc API

* **URL**: `{BASE_URL}/api/v1/customer_orders/{order_id}/received_form_fc`

* **Method:** `PUT`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
 requires :sno_chalan_id, type: Integer
 requires :order_ids, type: Array
```

* **Success Response:**
* **Code:** `200`
  	* **Content:**

```json
 {
   "success": true,
   "message": "successfully received for {distributor}",
   "status_code": 200
}
```

* **Error Response:**
* **Code:** `404`
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```

* **Error Response:**
* **Code:** `400`
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "{required_field} missing",
   "status_code": 400
}
```

Return Chalan received_from_dh API

* **URL**: `{BASE_URL}/api/v1/return_chalans/received_from_dh`

* **Method:** `POST`

*  **Headers:**
	 `Authorization: token`
	 
*  **Request Parameters:**
```
 requires :sno_return_chalan_id, type: Integer
 optional :returned_order_ids, type: Array
 optional :cancelled_order_ids, type: Array
    
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
* **Error Response:**
* **Code:** `400`
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "Returned_order_ids and Cancelled_order_ids are both empty",
   "status_code": 400
}
```

* **Error Response:**
* **Code:** `404`
  	* **If order not found to pack:**
  	* **Content:**
```json
{  "success" : false
   "message": "Order not found",
   "status_code": 404
}
```

* **Error Response:**
* **Code:** `400`
  	* **If any error occurred which is missing any required fields then:**
  	* **Content:**
```json
{  "success" : false
   "message": "sno_return_chalan_id missing",
   "status_code": 400
}
```
