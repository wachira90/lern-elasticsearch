# example command



````
DELETE mygeo

PUT mygeo
{  
  "settings": {
    "default_pipeline": "my_timestamp_pipeline"
  },
  "mappings": {
    "properties": {

      
      "jw": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword",
            "ignore_above": 256
          }
        }
      },

      "num": {
        "type": "long"
      },
        
      "location": {
        "type": "geo_point"
      },

      "tags": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword",
            "ignore_above": 256
          }
        }
      },      
      
      "date": {
        "type": "date",
        "format": "yyyy-MM-dd HH:mm:ss||yyyy-MM-dd||epoch_millis"
      }
    
    }
  }
}


PUT _ingest/pipeline/my_timestamp_pipeline
{
  "description": "Adds a field to a document with the time of ingestion",
  "processors": [
    {
      "set": {
        "field": "ingest_timestamp",
        "value": "{{_ingest.timestamp}}"
      }
    }
  ]
}




PUT mygeo/_doc/1
{
  "num" : 15,
 "jw": "Satun",
 "date":"2015-01-01",
 "location":{
   "lat": 6.546,
   "lon": 99.706
 }
}

DELETE mygeo/_doc/2

PUT mygeo/_doc/2
{
  "num" : 27,
 "jw": "Rayong",
 "date":"2015-01-11",
 "location":{
   "lat": 12.646,
   "lon": 101.171
 }
}

PUT mygeo/_doc/3
{
  "num" : 75,
 "jw": "Chumphon",
 "date":"2015-01-10",
 "location":{
   "lat": 10.459,
   "lon": 99.3403
 }
}

PUT mygeo/_doc/4
{
  "num" : 66,
 "jw": "Chumphon",
 "date":"2015-01-10",
 "location":{
   "lat": 10.459,
   "lon": 99.3403
 }
}

PUT /mygeo


GET /mygeo/_search?pretty=true
{
  "query": {
    "match": {
      "num": 27
    }
  }
}

GET /_tasks


GET /bemislog1-*/_search?pretty=true
{
  "query": {
    "match": {
      
      "tags" : "_jsonparsefailure"
    }
  }
}



GET _cat/shards?v=true&h=index,prirep,shard,store&s=prirep,store&bytes=gb


DELETE /test


PUT /test
{
  "settings": {
    "number_of_shards": 3,
    "number_of_replicas": 2
  },
  "mappings": {
    "properties": {
      "fname": { "type": "text" },
      "lname": { "type": "text" },
      "age": { "type": "double" }
    }
  }
}

GET usercsv/_search?pretty=true




PUT /stocks
{
  "settings": {
    "number_of_shards": 3,
    "number_of_replicas": 2
  },
  "mappings": {
    "properties": {
      "sname": {
        "type": "text"
      },
      "stype": {
        "type": "text"
      },
      "price1": {
        "type": "double"
      },
      "price2": {
        "type": "double"
      },
      "price3": {
        "type": "double"
      },
      "timestamp": {
        "type": "date",
        "format": "yyyy-MM-dd HH:mm:ss"
      }
    }
  }
}



GET stocks/_search
{
  "query": {
    "match_all": {}
  }
}



PUT stocks/_doc/1
{
  "sname": "SNC",
  "stype": "SET100",
  "price1": 22.25,
  "price2": 10.50,
  "price3": 5.50
}


PUT stocks/_doc/2
{
  "sname": "TNITY",
  "stype": "MAI",
  "price1": 7.25,
  "price2": 8.50,
  "price3": 9.50
}




POST _sql?format=json
{
  "query": """
  SELECT * FROM "stocks"
  """
}
````




