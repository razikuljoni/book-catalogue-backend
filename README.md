# Build a Book Catalogue Backend

## Main Part: API Endpoints and Sample Data:

## Implement Create, Read, Update, and Delete Operations for Users Listing

### User Sign Up

Route: https://books-catalogue.vercel.app/api/v1/auth/signup (POST)

Request body:

```json
{
    "name": "Admin Joni",
    "email": "admin@gmail.com",
    "password": "admin1234",
    "role": "admin",
    "contactNo": "01623208660",
    "address": "Dhaka, Bangladesh",
    "profileImg": "user.jpg"
}
```

Response: The newly created user object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 User created successfully",
    "data": {
        "id": "b6b99126-16f1-46ca-9afb-0ac92795caf0",
        "name": "Admin Joni",
        "email": "admin@gmail.com",
        "role": "admin",
        "contactNo": "01623208660",
        "address": "Dhaka, Bangladesh",
        "profileImg": "user.jpg"
    }
}
```

### User Sign In/Login

Route: https://books-catalogue.vercel.app/api/v1/auth/signin (POST)

Request body:

```json
{
    "email": "maruf@gmail.com",
    "password": "maruf1234"
}
```

Response: A object with user JWT token.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 User logged in successfully",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiIyOTUwZjBmNS1kZGJkLTQ0YjAtYmU4Mi05YWM1MGJhNWFiNDAiLCJpYXQiOjE2OTQwMDkwOTEsImV4cCI6MTcyNTU0NTA5MX0.xnWWCf7CDs2yWIgio4W5-djMjUhmy66Xf94Zhb3kO94"
}
```

Decoded Token:

```json
{
    "role": "customer",
    "userId": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
    "iat": 1694008811,
    "exp": 1725544811
}
```

### Get All Users → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/users (GET)

Request body:

Response: The user's array of objects.

Response Sample Data:

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Users fetched successfully",
    "data": [
        {
            "id": "b6b99126-16f1-46ca-9afb-0ac92795caf0",
            "name": "Admin Joni",
            "email": "admin@gmail.com",
            "role": "admin",
            "contactNo": "01623208660",
            "address": "Dhaka, Bangladesh",
            "profileImg": "user.jpg"
        },
        {
            "id": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
            "name": "Maruf Shahid",
            "email": "maruf@gmail.com",
            "role": "customer",
            "contactNo": "01943677233",
            "address": "Rangpur, Bangladesh",
            "profileImg": "user_maruf.jpg"
        }
        // More users
    ]
}
```

### Get a Single User → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 (GET)

Response: The specified user object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 User fetched successfully",
    "data": {
        "id": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
        "name": "Maruf Shahid",
        "email": "maruf@gmail.com",
        "role": "customer",
        "contactNo": "01943677233",
        "address": "Rangpur, Bangladesh",
        "profileImg": "user_maruf.jpg"
    }
}
```

### Update a Single User → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 (PATCH)

Request Body:

```json
{
    "name": "MD Maruf Shahid",
    "address": "Domar, Nilphamari."
}
```

Response: The updated user object.

Response Sample Pattern:

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 User updated successfully",
    "data": {
        "id": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
        "name": "MD Maruf Shahid",
        "email": "maruf@gmail.com",
        "role": "customer",
        "contactNo": "01943677233",
        "address": "Domar, Nilphamari.",
        "profileImg": "user_maruf.jpg"
    }
}
```

### Delete a User → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 ( DELETE)

Response: The deleted user object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 User deleted successfully",
    "data": {
        "id": "e535eb46-d957-4e08-9e89-e90b1842dd70",
        "name": "Abdullah Nayeen",
        "email": "nayeem@gmail.com",
        "role": "customer",
        "contactNo": "01943677000",
        "address": "Domar, Rangpur, Bangladesh",
        "profileImg": "user_nayeem.jpg"
    }
}
```

## Implement Create, Read, Update, and Delete Operations for Category Listing

### Create Category

Route: https://books-catalogue.vercel.app/api/v1/categories/create-category (POST) → Only Allowed For Admin

Request body:

```json
{
    "title": "Programming"
}
```

Response: The newly created category object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Category created successfully",
    "data": {
        "id": "434e97f6-498c-4aa5-97d9-e4fa39f4b531",
        "title": "Programming"
    }
}
```

### Get All Categories

Route: https://books-catalogue.vercel.app/api/v1/categories (GET)

Response: The categoryies array of objects.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 All Category fetched successfully",
    "data": [
        {
            "id": "434e97f6-498c-4aa5-97d9-e4fa39f4b531",
            "title": "Programming"
        },
        {
            "id": "858eca3c-1070-47a9-91ab-2bffb4a911cf",
            "title": "Horror"
        },
        {
            "id": "f52d345c-b804-4f78-82e7-904195b64a38",
            "title": "Thriller"
        },
        {
            "id": "8d7d395f-871b-47ac-9016-6ed14290531e",
            "title": "Drama"
        }
    ]
}
```

### Get a Single Category

Route: https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 (GET)

Response: The specified category object and books array of object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Single Category fetched successfully",
    "data": {
        "id": "f52d345c-b804-4f78-82e7-904195b64a38",
        "title": "Thriller",
        "books": [
            {
                "id": "7a31ec81-8843-48be-a768-fe16a3b335d4",
                "title": "The Girl with the Dragon Tattoo",
                "author": "Stieg Larsson",
                "price": "20.99",
                "genre": "Thriller",
                "publicationDate": "August 2005",
                "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
            },
            {
                "id": "b0dfecfb-5042-475f-8441-bea85fc4e1dd",
                "title": "Gone Girl",
                "author": "Gillian Flynn",
                "price": "25.99",
                "genre": "Thriller",
                "publicationDate": "June 2012",
                "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
            }
            // More books
        ]
    }
}
```

### Update a Category → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 (PATCH)

Request Param: :id

Request Body:

```json
{
    "title": "Fiction"
}
```

Response: The updated category object.

```json
{
    "success": true,
    "statusCode": 200,
    "message": "Category updated successfully",
    "data": {
        "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
        "title": "Fiction"
    }
}
```

### Delete a Category → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 ( DELETE)

Request Param: :id

Response: The deleted category object.

```json
{
    "success": true,
    "statusCode": 200,
    "message": "Category deleted successfully",
    "data": {
        "id": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d",
        "title": "Fiction"
    }
}
```

## Implement Create, Read, Update, and Delete Operations for Book listings.

### Create a New Book

Route: https://books-catalogue.vercel.app/api/v1/books/create-book (POST) → Only Allowed For Admin

Request body:

```json
{
    "title": "Little Women",
    "author": "Louisa May Alcott",
    "price": 35.22,
    "genre": "Drama",
    "publicationDate": "September 30, 1868",
    "categoryId": "8d7d395f-871b-47ac-9016-6ed14290531e"
}
```

Response: The newly created book object with category details.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Book created successfully",
    "data": {
        "id": "1cf9cd26-38b5-4ad2-9e94-73f870d0837d",
        "title": "Little Women",
        "author": "Louisa May Alcott",
        "price": "35.22",
        "genre": "Drama",
        "publicationDate": "September 30, 1868",
        "categoryId": "8d7d395f-871b-47ac-9016-6ed14290531e"
    }
}
```

### Get All Books

Route: https://books-catalogue.vercel.app/api/v1/books (GET)

Request body:

Response: The books array of objects with paginated metadata.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 All Books fetched successfully",
    "meta": {
        "page": 1,
        "size": 10,
        "total": 15,
        "totalPages": 2
    },
    "data": [
        {
            "id": "a2d6ff98-cc1d-4da8-9d66-9368c73a8b66",
            "title": "Algorithms",
            "author": "Robert Sedgewick and Kevin Wayne",
            "price": "25.22",
            "genre": "Programming",
            "publicationDate": "March 19, 2011",
            "categoryId": "434e97f6-498c-4aa5-97d9-e4fa39f4b531"
        },
        {
            "id": "b1e3b1d7-4af7-4998-80fa-37f1bf4d4dc8",
            "title": "Before I Go to Sleep",
            "author": "S.J. Watson",
            "price": "32.22",
            "genre": "Thriller",
            "publicationDate": "June 2011",
            "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
        }
        // More books...
    ]
}
```

### Get Books By CategoryId

Route: https://books-catalogue.vercel.app/api/v1/books/f52d345c-b804-4f78-82e7-904195b64a38/category (GET)

Request Param: :categoryId

Response: The books array of objects with paginated metadata.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Categorised Books fetched successfully",
    "meta": {
        "page": 1,
        "size": 10,
        "total": 6,
        "totalPages": 1
    },
    "data": [
        {
            "id": "7a31ec81-8843-48be-a768-fe16a3b335d4",
            "title": "The Girl with the Dragon Tattoo",
            "author": "Stieg Larsson",
            "price": "20.99",
            "genre": "Thriller",
            "publicationDate": "August 2005",
            "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
        },
        {
            "id": "b0dfecfb-5042-475f-8441-bea85fc4e1dd",
            "title": "Gone Girl",
            "author": "Gillian Flynn",
            "price": "25.99",
            "genre": "Thriller",
            "publicationDate": "June 2012",
            "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
        }
        // More books...
    ]
}
```

### Get a Single Book

Route: https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 (GET)

Request Param: :id

Response: The specified book object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Book fetched successfully",
    "data": {
        "id": "7a31ec81-8843-48be-a768-fe16a3b335d4",
        "title": "The Girl with the Dragon Tattoo",
        "author": "Stieg Larsson",
        "price": "20.99",
        "genre": "Thriller",
        "publicationDate": "August 2005",
        "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
    }
}
```

### Update a Single Book → Only Allowed For Admin

Route: https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 (PATCH)

Request Param: :id

Request Body:

```json
{
    "price": 30.99
}
```

Response: The updated book object.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Book updated successfully",
    "data": {
        "id": "7a31ec81-8843-48be-a768-fe16a3b335d4",
        "title": "The Girl with the Dragon Tattoo",
        "author": "Stieg Larsson",
        "price": "30.99",
        "genre": "Thriller",
        "publicationDate": "August 2005",
        "categoryId": "f52d345c-b804-4f78-82e7-904195b64a38"
    }
}
```

### Delete a book → Only Allowed for admins

Route: https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 ( DELETE)

Request Param: :id

Response: The deleted book object

```json
{
    "success": true,
    "statusCode": 200,
    "message": "Book is deleted successfully",
    "data": {
        "id": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
        "title": "The Catcher in the Rye Part-1",
        "author": "J.D. John",
        "genre": "Programming",
        "price": 340.75,
        "publicationDate": "1951-07-16",
        "categoryId": "b33e6c08-8b5e-47f5-b7cc-73f3b2f36a4d"
    }
}
```

## Implement Create, Read Operations for Order Listings.

### Create Order → Only Allowed For Customer

Route: https://books-catalogue.vercel.app/api/v1/orders/create-order (POST)

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiJkNjA4MDhkYS04NDBlLTRkOTMtODNlMS04ZGZmOTI1YWViZTIiLCJpYXQiOjE2OTQwNTg4MDUsImV4cCI6MTcyNTU5NDgwNX0.Xznu0-QIkuvWbu4JAuR0A7UD2TcStulik4Trbp3EvSU"

Decoded Token:

```json
{
    "role": "customer",
    "userId": "d60808da-840e-4d93-83e1-8dff925aebe2",
    "iat": 1694058805,
    "exp": 1725594805
}
```

Request Body:

```json
{
    "orderedBooks": [
        {
            "bookId": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
            "quantity": 3
        },
        {
            "bookId": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
            "quantity": 2
        }
    ]
}
```

Response: The newly created order object.

```json
{
    "success": true,
    "statusCode": 200,
    "message": "Order created successfully",
    "data": {
        "id": "fe659812-5b10-4b6d-b88d-7b9e60902a67",
        "userId": "b2e06b3e-87bf-4b11-a74a-29c66f8f48df",
        "orderedBooks": [
            {
                "bookId": "efb2949f-8f85-42f6-a9ce-8c177814e2ec",
                "quantity": 3
            },
            {
                "bookId": "c9b2d566-1d8a-4fe1-8d15-07ed4f7c5dc9",
                "quantity": 2
            }
        ],
        "status": "pending",
        "createdAt": "2023-08-28T10:00:00Z"
    }
}
```

### Get all Order → Only Allowed For Admins

Route: https://books-catalogue.vercel.app/api/v1/orders (GET)

Response: The ordered array of objects.

```json
{
    "success": true,
    "statusCode": 200,
    "message": "Orders retrieved successfully",
    "data": [
        {
            "id": "92e9d108-01cd-46fe-af99-e53092502e58",
            "userId": "d60808da-840e-4d93-83e1-8dff925aebe2",
            "orderedBooks": [
                {
                    "bookId": "b1e3b1d7-4af7-4998-80fa-37f1bf4d4dc8",
                    "quantity": 2
                },
                {
                    "bookId": "c995bffc-308c-493e-97b0-d39a916cd195",
                    "quantity": 1
                }
            ],
            "status": "pending",
            "createdAt": "2023-09-10T14:21:09.867Z"
        },
        {
            "id": "4b4da636-a35d-48bd-be81-fcbc8b1d1e3d",
            "userId": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
            "orderedBooks": [
                {
                    "bookId": "b1e3b1d7-4af7-4998-80fa-37f1bf4d4dc8",
                    "quantity": 2
                },
                {
                    "bookId": "c995bffc-308c-493e-97b0-d39a916cd195",
                    "quantity": 2
                }
            ],
            "status": "pending",
            "createdAt": "2023-09-10T16:02:02.252Z"
        }
        // More orders...
    ]
}
```

### Get all Order for specific Customers → Only Specific Customers

Route: https://books-catalogue.vercel.app/api/v1/orders (GET)

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiIyOTUwZjBmNS1kZGJkLTQ0YjAtYmU4Mi05YWM1MGJhNWFiNDAiLCJpYXQiOjE2OTQzNjE1MjUsImV4cCI6MTcyNTg5NzUyNX0.pa7XmdI51JHaKpD8f4fhgFXeEqyahq9_mk8MDsUxxt4"

Decoded Token:

```json
{
    "role": "customer",
    "userId": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
    "iat": 1694361525,
    "exp": 1725897525
}
```

Response: The ordered array of objects.

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Orders Data fetched successfully",
    "data": [
        {
            "id": "4b4da636-a35d-48bd-be81-fcbc8b1d1e3d",
            "userId": "2950f0f5-ddbd-44b0-be82-9ac50ba5ab40",
            "orderedBooks": [
                {
                    "bookId": "b1e3b1d7-4af7-4998-80fa-37f1bf4d4dc8",
                    "quantity": 2
                },
                {
                    "bookId": "c995bffc-308c-493e-97b0-d39a916cd195",
                    "quantity": 2
                }
            ],
            "status": "pending",
            "createdAt": "2023-09-10T16:02:02.252Z"
        }
        // More orders
    ]
}
```

# Bonus Part:

### Get single order by Id → Only for specific customer and admins

Route: https://books-catalogue.vercel.app/api/v1/orders/04684fd4-cdab-4fab-88b0-63d3e70fbfbd (Get)

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiY3VzdG9tZXIiLCJ1c2VySWQiOiJkNjA4MDhkYS04NDBlLTRkOTMtODNlMS04ZGZmOTI1YWViZTIiLCJpYXQiOjE2OTQwNTg4MDUsImV4cCI6MTcyNTU5NDgwNX0.Xznu0-QIkuvWbu4JAuR0A7UD2TcStulik4Trbp3EvSU"

Decoded Token:

```json
{
    "role": "customer",
    "userId": "d60808da-840e-4d93-83e1-8dff925aebe2",
    "iat": 1694058805,
    "exp": 1725594805
}
```

Sample Response Data:

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Order Data fetched successfully",
    "data": [
        {
            "id": "04684fd4-cdab-4fab-88b0-63d3e70fbfbd",
            "userId": "d60808da-840e-4d93-83e1-8dff925aebe2",
            "orderedBooks": [
                {
                    "bookId": "b1e3b1d7-4af7-4998-80fa-37f1bf4d4dc8",
                    "quantity": 1
                },
                {
                    "bookId": "c995bffc-308c-493e-97b0-d39a916cd195",
                    "quantity": 1
                }
            ],
            "status": "pending",
            "createdAt": "2023-09-10T15:57:23.355Z"
        }
    ]
}
```

### Get User Profile Data → Only for specific user (customer and admin)

Route: https://books-catalogue.vercel.app/api/v1/profile (Get)

Request Headers: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiYWRtaW4iLCJ1c2VySWQiOiJiNmI5OTEyNi0xNmYxLTQ2Y2EtOWFmYi0wYWM5Mjc5NWNhZjAiLCJpYXQiOjE2OTQwMDkzOTQsImV4cCI6MTcyNTU0NTM5NH0.nNYOgMpKmVQogNJ-TsS09WImF5m99e5DkjhOgtkNILU"

Decoded Token:

```json
{
    "role": "admin",
    "userId": "b6b99126-16f1-46ca-9afb-0ac92795caf0",
    "iat": 1694009394,
    "exp": 1725545394
}
```

Response:

```json
{
    "statusCode": 200,
    "success": true,
    "message": "🆗 Profile fetched successfully",
    "data": {
        "id": "b6b99126-16f1-46ca-9afb-0ac92795caf0",
        "name": "Admin Joni",
        "email": "admin@gmail.com",
        "password": "$2b$10$A/1PN0CDb3BYpjee9cHL5uX100UJqs7joyRAHhKCa50Y6P949u5V2",
        "role": "admin",
        "contactNo": "01623208660",
        "address": "Dhaka, Bangladesh",
        "profileImg": "user.jpg"
    }
}
```

## Live Link: https://books-catalogue.vercel.app/api/v1

### Application Routes:

### User

-   https://books-catalogue.vercel.app/api/v1/auth/signup (POST)
-   https://books-catalogue.vercel.app/api/v1/auth/signin (POST)
-   https://books-catalogue.vercel.app/api/v1/users (GET)
-   https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 (Single GET)
-   https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 (PATCH)
-   https://books-catalogue.vercel.app/api/v1/users/2950f0f5-ddbd-44b0-be82-9ac50ba5ab40 (DELETE)
-   https://books-catalogue.vercel.app/api/v1/profile (GET)

### Category

-   https://books-catalogue.vercel.app/api/v1/categories/create-category (POST)
-   https://books-catalogue.vercel.app/api/v1/categories (GET)
-   https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 (Single GET)
-   https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 (PATCH)
-   https://books-catalogue.vercel.app/api/v1/categories/f52d345c-b804-4f78-82e7-904195b64a38 (DELETE)

### Books

-   https://books-catalogue.vercel.app/api/v1/books/create-book (POST)
-   https://books-catalogue.vercel.app/api/v1/books (GET)
-   https://books-catalogue.vercel.app/api/v1/books/f52d345c-b804-4f78-82e7-904195b64a38/category (GET)
-   https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 (GET)
-   https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 (PATCH)
-   https://books-catalogue.vercel.app/api/v1/books/7a31ec81-8843-48be-a768-fe16a3b335d4 (DELETE)

### Orders

-   https://books-catalogue.vercel.app/api/v1/orders/create-order (POST)
-   https://books-catalogue.vercel.app/api/v1/orders (GET)
-   https://books-catalogue.vercel.app/api/v1/orders/04684fd4-cdab-4fab-88b0-63d3e70fbfbd (GET)
