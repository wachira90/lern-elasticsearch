# COMMAND ON DEVTOOLS

````
# CREATE SCHEMA
PUT user
{
  "mappings": {
    "properties": {
      "fname": { "type": "text" },
      "lname": { "type": "text" },
      "age" : {"type" : "double"},
      "timestamp" : {"type" : "date"}
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


# INSERT 1
PUT user/_doc/1
{
  "fname": "Wachira",
  "lname": "Duangdee",
  "age": 36,
  "timestamp": "2022-04-21T10:59:27.109330"
}


# INSERT 2
PUT user/_doc/2
{
  "fname": "John",
  "lname": "Doe",
  "age": 26,
  "timestamp": "2022-04-21T11:59:27.109330"
}


# INSERT 3
PUT user/_doc/3
{
  "fname": "Sam",
  "lname": "molin",
  "age": 40,
  "timestamp": "2022-04-21T12:50:18.947427"
}


# UPDATE 3
PUT user/_doc/3
{
  "fname": "Kman",
  "lname": "Green",
  "age": 66,
  "timestamp": "2022-04-21T12:50:18.947427"
}


# DELETE DOC 3
DELETE user/_doc/3


# DELETE ALL INDEX 'user'
DELETE user


# SEARCH 
GET user/_search
{
    "query": {
        "match": {
            "fname":"*hn"
        }
    }
}

````


# COMMAND HTTP (REST CLIENT VSCODE)

````

###
GET http://172.16.1.5:9200/user/_search?pretty=true&size=10000&from=0&sort=timestamp:desc

###
GET  http://172.16.1.5:9200/user/_search?pretty=true

###
GET http://172.16.1.5:9200/user/_search?pretty=true&q=%22john%22

###
GET http://172.16.1.5:9200/user/_search?pretty=true&q=%22age=45%22

###
GET http://172.16.1.5:9200/user/_search?pretty=true&q=%22wachira%22


### SEARCH ALL
GET http://172.16.1.5:9200/user/_search
Content-Type: application/json

{
    "query": {
        "match_all": {}
    }
}


### SEARCH AGE 45
GET http://172.16.1.5:9200/user/_search
Content-Type: application/json

{
    "query": {
        "match": {
            "fname":"john"
            // "age":45
        }
    }
}
````


