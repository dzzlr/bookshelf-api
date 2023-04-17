# Requirement
- [x] Application run on port 9000
- [x] Application must be run with command `npm run start`
- [x] API can [store books](# Get All Books)
- [x] API can [display entire books](# Store Books)
- [x] API can [display book details](# Get a Book by id)
- [x] API can [modify book data](# Update a Book by id)
- [x] API can [delete books](# Delete a Book by id)

# Model for Payload
```json
{
    "name": string,
    "year": number,
    "author": string,
    "summary": string,
    "publisher": string,
    "pageCount": number,
    "readPage": number,
    "reading": boolean
}
```

# Example Response
```json
{
    "id": "Qbax5Oy7L8WKf74l",
    "name": "Buku A",
    "year": 2010,
    "author": "John Doe",
    "summary": "Lorem ipsum dolor sit amet",
    "publisher": "Dicoding Indonesia",
    "pageCount": 100,
    "readPage": 25,
    "finished": false,
    "reading": false,
    "insertedAt": "2021-03-04T09:11:44.598Z",
    "updatedAt": "2021-03-04T09:11:44.598Z"
}
```

Properti yang ditebalkan diolah dan didapatkan di sisi server. Berikut penjelasannya:
- `id` : nilai `id` haruslah unik. Untuk membuat nilai unik, Anda bisa memanfaatkan `nanoid`.
- `finished` : merupakan properti boolean yang menjelaskan apakah buku telah selesai dibaca atau belum. Nilai `finished` didapatkan dari observasi `pageCount === readPage`.
- `insertedAt` : merupakan properti yang menampung tanggal dimasukkannya buku. Anda bisa gunakan `new Date().toISOString()` untuk menghasilkan nilainya.
- `updatedAt` : merupakan properti yang menampung tanggal diperbarui buku. Ketika buku baru dimasukkan, berikan nilai properti ini sama dengan `insertedAt`.

# RESTful API Criteria
## Get All Books
| **Method** | **Route**  | **Name**                     |
|------------|------------|------------------------------|
| GET        | /books     | Get All Books                |

Sample Response
```json
{
    "status": "success",
    "data": {
        "books": [
            {
                "id": "Qbax5Oy7L8WKf74l",
                "name": "Buku A",
                "publisher": "Dicoding Indonesia"
            },
            {
                "id": "1L7ZtDUFeGs7VlEt",
                "name": "Buku B",
                "publisher": "Dicoding Indonesia"
            },
            {
                "id": "K8DZbfI-t3LrY7lD",
                "name": "Buku C",
                "publisher": "Dicoding Indonesia"
            }
        ]
    }
}
```

Sample Response 

## Store Books
| **Method** | **Route**  | **Name**                     |
|------------|------------|------------------------------|
| POST       | /books     | Add Books                    |

## Get a Book by id
| **Method** | **Route**  | **Name**                     |
|------------|------------|------------------------------|
| GET        | /books/:id | Get a Detail Book With ID    |

Success Response
```json
{
    "status": "success",
    "data": {
        "book": {
            "id": "aWZBUW3JN_VBE-9I",
            "name": "Buku A Revisi",
            "year": 2011,
            "author": "Jane Doe",
            "summary": "Lorem Dolor sit Amet",
            "publisher": "Dicoding",
            "pageCount": 200,
            "readPage": 26,
            "finished": false,
            "reading": false,
            "insertedAt": "2021-03-05T06:14:28.930Z",
            "updatedAt": "2021-03-05T06:14:30.718Z"
        }
    }
}
```

Failed Response
```json
{
    "status": "fail",
    "message": "Buku tidak ditemukan"
}
```

## Update a Book by id
| **Method** | **Route**  | **Name**                     |
|------------|------------|------------------------------|
| PUT        | /books/:id | Update a Detail Book With ID |

Success Response
```json
{
    "status": "success",
    "message": "Buku berhasil diperbarui"
}
```

Failed Response
```json
{
    "status": "fail",
    "message": "Gagal memperbarui buku. Mohon isi nama buku"
}
```

## Delete a Book by id
| **Method** | **Route**  | **Name**                     |
|------------|------------|------------------------------|
| DELETE     | /books/:id | Delete a Book With ID        |

Success Response
```json
{
    "status": "success",
    "message": "Buku berhasil dihapus"
}
```

Failed Response
```json
{
    "status": "fail",
    "message": "Buku gagal dihapus. Id tidak ditemukan"
}
```
