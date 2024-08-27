
/handleCustomers


/handleCustomers?action=add

/handleCustomers?action=getall


/customers/{id}

<customer>
  <id>1</id>
  <name>some name</name>
</customer>

{
  id: 1,
  name: 'some name'
}

HTTP ?

Any client can understand and consume




1. Write a JSON object representing a Customer. The customer should have an Id (string), name (string), active status (boolean).

```json
{
  "id": "1",
  "name": "some name",
  "activeStatus": true
}
```

2. Customer should have Order IDs (Unique identifiers for each order).
array -> []
{
  "id": "1",
  "name": "some name",
  "activeStatus": true,
  "orderIds": [1, 2, 3]
}

3. Add address to Customer schema. Address should have street (string), city (string), state (string), postalcode (number) and country (string)
object -> dictionary -> {}

```json
{
  "id": "1",
  "name": "some name",
  "activeStatus": true,
  "orderIds": [1, 2, 3],
  "address": {
    "street": "some street",
    "city": "some city",
    "state": "some state",
    "postalcode": 123456,
    "country": "some country"
  }
}
```

Exercise
------------
Write a JSON object representing a blog post. The post should have an Id (number) and title (string).

GET /posts/{id}
```json
{
  "id": 1,
  "title": "blog title-1"
}
```

- Create a representation of several blogs:
GET /posts

```json
{
  "posts": [
    {
      "id": 1,
      "title": "blog title-1"
    },
    {
      "id": 2,
      "title": "blog title-2"
    },
  ]
}
```

- People reading blogs wants to comment, add comments. We want a list of comments. Defining a single comment

GET /comments/{id}

```json
{
  "id": 1,
  "text": "some comment",
  "postId": 1
}
```

- create multiple comments structure
GET /comments
```json
{
  "comments": [
    {
      "id": 1,
      "text": "some comment",
      "postId": 1
    },
    {
      "id": 2,
      "text": "some comment-2",
      "postId": 1
    },
    {
      "id": 3,
      "text": "some comment-3",
      "postId": 2
    }
  ]
}
```

- Get me a blog post
```json
{
  "id": 1,
  "title": "blog title-1"
}
```

- Get me a blog post with comments
GET /posts/{id} -> how to tell the server that we want comments embedded in response?

GET /posts/1?_embed=comments

```json
{
  "id": 1,
  "title": "blog title-1",
  "comments": [
    {
      "id": 1,
      "text": "some comment"
    },
    {
      "id": 2,
      "text": "some comment-2"
    }
  ]
}
```


/post
/customer
/user
/comment

Verbs - CRUD
GET, POST, PUT, DELETE

verbs + nouns = meaning

GET /posts -> get all posts
GET /posts/{id} -> get the post with ID as 1
    /posts/1

POST /posts -> add a new post, client should send the request body

PUT/PATCH /posts/{id} -> update a post

DELETE /posts/{id} -> delete a post

/posts/1/comments -> all comments related to post 1


POST /posts
request 
{
  "title": "blog title-1"
}

response:
{
  "id": 1,
  "title": "blog title-1"
}

PATCH/PUT /posts/1
{
  "title": "NEW blog title-1"
}