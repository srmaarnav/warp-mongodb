# warp-mongodb

You can then use CRUD operations on the book resource like this:

Fetch all books:

```bash
curl http://localhost:8080/book
```

Create a new book:

```bash
curl -X POST http://localhost:8080/book -d '{"name": "The Lean Startup", "author": "Eric Ries", "num_pages": 480, "tags": ["non-fiction", "startup"]}' -H "content-type: application/json"
```

Edit a book:

```bash
curl -X PUT http://localhost:8080/book/5f15fd5400b98edc001944c0 -d '{"name": "The Lean Way", "author": "Eric Ries", "num_pages": 650, "tags": ["non-fiction", "business"]}' -H "content-type: application/json"
```

Delete a new book:

```bash
curl -X DELETE http://localhost:8080/book/5f15fd3900789205001944bf
```