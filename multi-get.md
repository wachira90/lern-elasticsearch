# multi get index



````
GET /_mget
{
  "docs": [
    {
      "_index": "my-index-000001",
      "_id": "1"
    },
    {
      "_index": "my-index-000001",
      "_id": "2"
    }
  ]
}
````

## Request
````
GET /_mget

GET /<index>/_mget
````
