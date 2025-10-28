```mermaid
erDiagram
    category {
        serial id PK
        varchar(25) name
    }

    bookshelf {
        serial id PK
        varchar(15) code
        int category_id FK
    }

    books {
        serial id PK
        varchar(50) title
        varchar(25) author
        int bookshelf_id FK
    }

    librarians {
        serial id PK
        varchar(25) name
    }

    members {
        serial id PK
        varchar(25) name
    }

    borrowing {
        serial id PK
        int book_id FK
        int member_id FK
        int librarian_id FK
        timestamp created_at
    }

    category ||--o{ bookshelf : "has"
    bookshelf ||--o{ books : "contains"
    books ||--o{ borrowing : "borrowed in"
    members ||--o{ borrowing : "borrows"
    librarians ||--o{ borrowing : "processes"