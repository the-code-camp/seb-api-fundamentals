
/manageCustomer?action=get

/manageCustomer?action=add


/customers/{id}

/customers/1
/customers/2

<customer>
  <id>1</id>
  <name>some name</name>
</customer>

{
  "id": 1,
  "name": "some name"
}

"1","some name"




Exercise
-----------
1. Write a JSON object representing a Customer. The customer should have an Id (string), name (string), active status (boolean).

```json
{
  "id": "1",
  "name": "some name",
  "status": false
}
```

2. Customer should have Order IDs (Unique identifiers for each order).

```json
{
  "id": "1",
  "name": "some name",
  "status": false,
  "orderIds": ["1", "2", "3"]
}
```

3. Add address to Customer object. Address should have street (string), city (string), state (string), postalcode (number) and country (string)

```json
{
  "id": "1",
  "name": "some name",
  "status": false,
  "orderIds": ["1", "2", "3"],
  "address": {
    "street": "some street",
    "city": "some city",
    "state": "some state",
    "postalcode": 123456,
    "country": "some country"
  }
}
```

Blog:
---------
posts, author, feedback, id, image, links

Exercise
-----------
Write a JSON object representing a blog post. The post should have an Id (string) and title (string).

```json
{
  "id": "1",
  "title": "some title-1"
}
```

- Create a representation of several blogs:
GET /posts
```json
{
  "posts": [
    {
      "id": "1",
      "title": "some title-1"
    },
    {
      "id": "2",
      "title": "some title-2"
    }
  ]
}
```

- People reading blogs wants to comment, add comments. We want a list of comments. Define a single comment.
GET /comments/1
```json
{
  "id": "1",
  "postId": "1",
  "text": "comment"
}
```

- create multiple comments structure
GET /comments
```json
{
  "comments": [
    {
      "id": "1",
      "postId": "1",
      "text": "comment one"
    },
    {
      "id": "2",
      "postId": "1",
      "text": "comment two"
    },
    {
      "id": "3",
      "postId": "2",
      "text": "comment three"
    }
  ]
}
```

- Get me a blog post
GET /posts/1
```json
{
  "id": "1",
  "title": "some title-1"
}
```

- Get me a blog post with comments. Can we express it through URL?
GET /posts/1?_embed=comments

```json
{
  "id": "1",
  "title": "some title-1",
  "comments": [
    {
      "id": "1",
      "postId": "1",
      "text": "comment one"
    },
    {
      "id": "2",
      "postId": "1",
      "text": "comment two"
    }
  ]
}
```


/posts -> nouns
/customers 
/users

verbs + nouns = meaningful (CRUD)

Verbs GET, POST, PUT/PATCH, DELETE, HEAD, OPTIONS, TRACE
CRUD

GET /posts -> get all posts state from the server
GET /posts/1 -> get the state of the postId 1
GET /posts/2 -> get the state of the postId 2

POST /posts -> Add a new post

PUT /posts/{id} -> Update/Add a new post (UPSERT)
PATCH /posts/{id} -> Update an existing post

DELETE /posts/{id} -> deletes a post

GET /comments

Relationships in the URL
GET /posts/1/comments -> get all comments related to postId 1

GET /comments/1/posts







/posts

New path /posts/{postId}

GET   /posts
POST  /posts

GET   /posts/10 -> 404

fetch(url)
.success((response)=> {
  // 2XX needs to be handled here
})
.error((error) => {
  // 4xx, 5xx needs to be handled here
})


/posts/10?_embed=comments

GET /posts/10
PUT/PATCH /posts/10
DELETE /posts/10



class Customer {
  Address address
  Orders orders
}

class Address {

}

class Orders {
  
}

