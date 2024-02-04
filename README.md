# API Documentation

### User Module

1. User Profile API
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



### Book Exchange Module

1.  Request for Book Exchange <br>
    **Description** - Request for book access from a issuer 
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

2. Get Approval List of books <br>
    **Description** - Get a list of pending approvals
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
