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


## request


````
GET /_mget

GET /<index>/_mget
````


## example


````
# GET MULTI WITH INDEX
GET user/_mget
{
  "docs": [
    {
      "_id": "3"
    },
    {
      "_id": "2"
    }
  ]
}


# GET MULTI 
GET _mget/
{
  "docs": [
    {
      "_index": "user",
      "_id": "3"
    },
    {
      "_index": "user",
      "_id": "2"
    }
  ]
}
````


## filter


````
GET /_mget
{
  "docs": [
    {
      "_index": "test",
      "_id": "1",
      "_source": false
    },
    {
      "_index": "test",
      "_id": "2",
      "_source": [ "field3", "field4" ]
    },
    {
      "_index": "test",
      "_id": "3",
      "_source": {
        "include": [ "user" ],
        "exclude": [ "user.location" ]
      }
    }
  ]
}
````


