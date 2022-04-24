# create index pattern

````
PUT /user
{
  "settings": {
    "number_of_shards": 3,
    "number_of_replicas": 2
  },
  "mappings": {
    "properties": {
      "fname": {
        "type": "text"
      },
      "lname": {
        "type": "text"
      },
      "age": {
        "type": "double"
      },
      "timestamp": {
        "type": "date",
        "format": "yyyy-MM-dd HH:mm:ss||yyyy-MM-dd||epoch_millis"
      }
    }
  }
}



# GET ALL DATA
GET user/_search
{
  "query": {
    "match_all": {}
  }
}



# INSERT
PUT user/_doc/1
{
  "fname": "Wachira",
  "lname": "Duangdee",
  "age": 36,
  "timestamp": "2022-04-21T10:59:27.109330"
}


# INSERT
PUT user/_doc/2
{
  "fname": "John",
  "lname": "Doe",
  "age": 26,
  "timestamp": "2022-04-21T11:59:27.109330"
}


# INSERT
PUT user/_doc/3
{
  "fname": "Sam",
  "lname": "molin",
  "age": 40,
  "timestamp": "2022-04-21T12:50:18.947427"
}


# INSERT
PUT user/_doc/4
{
  "fname": "Donny",
  "lname": "Yen",
  "age": 43,
  "timestamp": "2022-04-21T15:50:18.947427"
}


# UPDATE
PUT user/_doc/3
{
  "fname": "Kman",
  "lname": "Green",
  "age": 40,
  "timestamp": "2022-04-21T12:50:18.947427"
}


# DELETE
DELETE user/_doc/3


# DELETE ALL INDEX
DELETE user


# SEARCH 
GET user/_search
{
    "query": {
        "match": {
            "fname":"john"
        }
    }
}


# SORT
GET user/_search
{
  "sort": { "timestamp": "desc"} 
}

````

info data type : https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html
