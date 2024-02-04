# API Documentation

### User Module

1. **Register API**
    Description - Register User and ask the user to select interested topics
    ```
    REQUEST URL: {{HOST}}/user/register-user/
    REQUEST METHOD: POST
    REQUEST PAYLOAD: 
    {
        "username": "ssrakshith2301",
        "password": "abc123",
        "interests": ["drama", "True Crime"],
        "postal_address": "#30, 100ft Road, Indiranagar",
        "email": "john.doe21@exampl3e.com",
        "phone_no": "1234567890"
    }
    RESPONSE:
    {
        "message": "Successfully registered user"
    }
    ```
2. **Login API**
    Description - API Endpoint gives a token
    ```
    REQUEST URL: {{HOST}}/user/login-user/
    METHOD: POST
    PAYLOAD:
    {
        "email": "john.doe21@example.com",
        "password": "abc123"
    }

    RESPONSE:
    {
        "message": "Login Successful",
        "data": {
            "access_token": "eIkpXVCJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoyMzdmODhiNjY3IiwidXNlcl9pZCI6Mn0.uXcBQlsc2AhIrumCgv1y-p_6F7XtJ2MjMWDl0WV2Ckg"
        }
    }

    ```

3. User Profile API
    Description - Get the user uploaded books
    ````
        REQUEST URL: {{HOST}}/user/user-profile/<int:user_id>
        REQUEST METHOD: GET
        RESPONSE: 
            {
            "message": "success",
            "data": {
                "username": "ssrakshith",
                "short_description": "",
                "books_uploaded_by_user": [
                    {
                        "created_at": "2024-02-03T13:23:33.866888Z",
                        "updated_at": "2024-02-03T13:23:33.866929Z",
                        "book_name": "Sherlock Holmes",
                        "added_by_user_ids": [
                            2
                        ],
                        "description": "Detective Novel",
                        "added_by_users": [
                            "Rakshith"
                        ],
                        "rating": 4,
                        "id": 2
                    },
                    ...
                    {
                        "created_at": "2024-02-03T13:24:55.494955Z",
                        "updated_at": "2024-02-03T13:24:55.494986Z",
                        "book_name": "Rich Dad, Poor Dad",
                        "added_by_user_ids": [
                            2
                        ],
                        "description": "Book About Investing",
                        "added_by_users": [
                            "Rakshith"
                        ],
                        "rating": 4,
                        "id": 4
                    }
                ]
            }
        }
    ````
4. Wallet Detail 
    ```
    REQUEST URL: {{HOST}}/user/wallet-details/
    REQUEST HEADERS: Authorization Bearer {{token}}
    REQUEST METHOD: GET
    API RESPONSE:
    {
        "message": "success",
        "wallet_balance": 50,
        "user_id": 2,
        "username": "ssrakshith"
    }

    ```


### Book Exchange Module

1.  **Request for Book Exchange** <br>
    Description - Request for book access from a issuer 
    ```
    REQUEST URL: {{HOST}}/book-listing/request-for-book/
    REQUEST METHOD:  POST
    REQUEST HEADERS: Authorization Bearer {{token}}
    REQUEST PAYLOAD: 
     {
         "user_id": 2,
         "book_id": 1
     }
     RESPONSE: 
     {
         "message": "success"
     }
    ````

2. **Get Approval List of books** <br>
    Description - Get a list of pending approvals
    ```
        REQUEST URL: {{HOST}}/book-listing/approval-list/
        REQUEST METHOD: GET
        RESPONSE: 
            {
            "message": "success",
            "data": [
                {
                    "request_id": "7821e2f2bf0d45a0a7f18853d54b6b1e",
                    "created_at": "2024-02-03T13:24:55.494955Z",
                    "updated_at": "2024-02-03T13:24:55.494986Z",
                    "book_name": "Rich Dad, Poor Dad",
                    "added_by_user_ids": [
                        2
                    ],
                    "description": "Book About Investing",
                    "added_by_users": [
                        "Rakshith"
                    ],
                    "rating": 4,
                    "id": 4
                }
                ]
            }
    ```

3. **Approve a book for exchange** <br>
    Description - Approve a book for exchange and deduct coins from borrowers wallet.
    ```
    REQUEST URL: {{HOST}}/book-listing/approval-list/
    REQUEST METHOD: GET
    REQUEST HEADERS: Authorization Beare {{token}}
    REQUEST PAYLOAD:
    {
        "request_id": "dafd770432b34ec3a14f22fdd67f341f"
    }
    RESPONSE:
    {
        "message": "success"
    }
    ```

4. **Add Books** <br>
    Description - Add books with topics
    ```
    REQUEST URL: {{HOST}}/book-listing/add-books/
    REQUEST HEADERS: Authorization Bearer {token}
    PAYLOAD:
    {
        "book_name": "Ikigai: The Japanese Secret to a Long and Happy Life",
        "author_name": "Francesc Miralles and Hector Garcia",
        "description": "According to the Japanese, everyone has an ikigai",
        "rating": 4
    }

    RESPONSE:
    {
        "message": "success"
    }
    ```

5. **Get Books List** <br>
    Description - Get a list of books.
    ```
    REQUEST URL: {{HOST}}/book-listing/get-books/
    REQUEST METHOD: GET
    API RESPONSE:
    {
        "message": "success",
        "data": [
            {
                "created_at": "2024-02-04T07:40:02.478117Z",
                "updated_at": "2024-02-04T07:40:02.478147Z",
                "book_name": "Sherlock Holmes",
                "added_by_user_ids": [
                    2
                ],
                "description": "Investigative Tales about Sherlock Holmes and Dr. Watson",
                "added_by_users": [
                    "ssrakshith"
                ],
                "rating": 4,
                "id": 24,
                "added_by_users_list": [
                    {
                        "ssrakshith": 2
                    }
                ]
            },
        ]
    }
    ```

6. Personal Recommendations - Get User Recommendations based on topics

    ```
    REQUEST URL: {{HOST}}/book-listing/get-personal-recommendations/
    REQUEST HEADERS: Authorization Bearer {token}
    REQUEST METHOD: GET
    PAYLOAD: 
    {
        "message": "success",
        "data": [
            {
                "created_at": "2024-02-03T18:45:18.518194Z",
                "updated_at": "2024-02-03T18:45:18.518218Z",
                "book_name": "We are anonymous",
                "added_by_user_ids": [
                    4
                ],
                "description": "Deep dive into hacker group - Anonymous and",
                "added_by_users": [
                    "ssrakshith23"
                ],
                "rating": 4,
                "id": 6
            }
        ]
    }

    ```
