## CRUD Product App

This project includes a sample application that uses Amazon DynamoDB to perform CRUD operations

### Interface and Data Flow

The project structure base on interface transportation and transformation. All the data transformation methods are written without using plugins. Interfaces follow

```
type Interface interface {
	Get(w http.ResponseWriter, r *http.Request)
	Post(w http.ResponseWriter, r *http.Request)
	Put(w http.ResponseWriter, r *http.Request)
	Delete(w http.ResponseWriter, r *http.Request)
	Options(w http.ResponseWriter, r *http.Request)
}
```

Data flow (`internal` folder)

```
routes ➡  handlers ➡ controllers ➡ entities
```

### Package index

List dependencies used in this system by using [github.com/ribice/glice](https://github.com/ribice/glice), a Golang license and dependency checker. The package prints list of all dependencies, their URL, license and saves all the license files in /licenses

```
+---------------------------------------+--------------------------------------------+--------------+
|              DEPENDENCY               |                  REPOURL                   |   LICENSE    |
+---------------------------------------+--------------------------------------------+--------------+
| github.com/go-chi/cors                | https://github.com/go-chi/cors             | MIT          |
| github.com/aws/aws-sdk-go             | https://github.com/aws/aws-sdk-go          | Apache-2.0   |
| github.com/go-chi/chi/v5              | https://github.com/go-chi/chi              | MIT          |
| github.com/go-ozzo/ozzo-validation/v4 | https://github.com/go-ozzo/ozzo-validation | MIT          |
| github.com/google/uuid                | https://github.com/google/uuid             | bsd-3-clause |
+---------------------------------------+--------------------------------------------+--------------+
```

### Endpoints

-   HealthCheck provided
    -   Endpoint: `/health`
    -   Request: GET request
    -   Input: None
    -   Output: The status of the server

The Product struct is used to perform the following CRUD operations:

-   Create:
    -   Endpoint: `/product`
    -   Request: `POST` request
    -   Input: Client passes in the new object's properties via JSON body
    -   Output: A new object is created in the database
-   ListOne:
    -   Endpoint: `/product/{ID}`
    -   Request: `GET` request
    -   Input: Client passes in the name object to be retrieved via endpoint field
    -   Output: All the fields of the object are outputted to the console
-   ListAll:
    -   Endpoint: `/product`
    -   Request: `GET` request
    -   Input: None
    -   Output: All the objects are outputted to the console
-   Delete:
    -   Endpoint: `/product/{ID}`
    -   Request: `GET` request
    -   Input: Client passes in the name of the object to be deleted via endpoint field
    -   Output: Object is deleted from the database
-   Update:
    -   Endpoint: `/product/{ID}`
    -   Request: `PUT` request
    -   Input: Client passes in the new object's properties via JSON body and the name of the object to be edited via JSON body
    -   Output: All the fields of the object are outputted to the console and the values of the object are edited in the database
