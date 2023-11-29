
# Microservices-Based Note-Taking Application

A microservice application of two Microservices: User Management, Note Management. Each microservice with a separate database both in MySQL database.
These two Microservices communicate with eachother with two ways: Internal api calls, Message broker using RabbitMQ.


## Communication

The communication between services happens in two ways Synchronous and Asynchronous.
In Synchronous way: I used internal api calls to validate the token passed in the note management microservice endpoints as i need to wait to check if the user is authenticated. While in Asynchronous way: I used RabbitMQ as i dont need to wait for the response. Used when a new user is created to save the new user in the note management microservice.


----------

## API Reference for User Management microservice
### Base URL: http://localhost:8000

#### Register a new user

```http
  POST /api/auth/register
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `name` | `string` | **Required**.  |
| `email` | `string` | **Required**.  |
| `password` | `string` | **Required**.  |
| `password_confirmation` | `string` | **Required**.  |


#### Login with email and password

```http
  POST /api/auth/login
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `email` | `string` | **Required**.  |
| `password` | `string` | **Required**.  |

#### Get item

```http
  GET /api/auth/logout
```
Request Header

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	          | Authorization    	     | Bearer {JWT}      	    |




----------

## API Reference for Note Management microservice
### Base URL: http://localhost:8001

#### List authenticated user's notes

```http
  GET /api/note
```
#### Request Headers

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	     | Authorization    	     | Bearer {JWT}      	    |

#### Select note by ID

```http
  GET /api/note/{id}
```
#### Request Headers

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	     | Authorization    	     | Bearer {JWT}      	    |

#### Store a new note

```http
  POST /api/note
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `title` | `string` | **Required**.  |
| `content` | `string` | **Required**.  |


Request Header

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	          | Authorization    	     | Bearer {JWT}      	    |

#### Update note by ID [PUT]

```http
  PUT /api/note
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `title` | `string` | **Required**.  |
| `content` | `string` | **Required**.  |


Request Header

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	          | Authorization    	     | Bearer {JWT}      	    |

#### Update note by ID [PATCH]

```http
  PATCH /api/note
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `title` | `string` | **Optional**.  |
| `content` | `string` | **Optional**.  |


Request Header

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	          | Authorization    	     | Bearer {JWT}      	    |

#### Delete note by ID

```http
  DELETE /api/note/{id}
```
#### Request Headers

| **Required** 	 | **Key**              	 | **Value**            	 |
|----------------|------------------------|------------------------|
| Yes      	     | Content-Type     	     | application/json 	     |
| Yes 	     | Authorization    	     | Bearer {JWT}      	    |



