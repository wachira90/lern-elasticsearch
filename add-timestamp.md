# add timestamp

## code
````
PUT mymap
{
  "settings": {
    "default_pipeline": "my_timestamp_pipeline"
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

PUT mymap/_doc/1
{
  "num" : 15,
 "jw": "Satun",
 "location":{
   "lat": 6.546,
   "lon": 99.706
 }
}


PUT mymap/_doc/2
{
  "num" : 27,
 "jw": "Rayong",
 "location":{
   "lat": 12.646,
   "lon": 101.171
 }
}


PUT mymap/_doc/3
{
  "num" : 75,
 "jw": "Chumphon",
 "location":{
   "lat": 10.459,
   "lon": 99.3403
 }
}
````

## output 

````
{
  "took" : 0,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 3,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "mymap",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "num" : 15,
          "location" : {
            "lon" : 99.706,
            "lat" : 6.546
          },
          "ingest_timestamp" : "2022-02-05T10:15:58.247Z",
          "jw" : "Satun"
        }
      },
      {
        "_index" : "mymap",
        "_type" : "_doc",
        "_id" : "2",
        "_score" : 1.0,
        "_source" : {
          "num" : 27,
          "location" : {
            "lon" : 101.171,
            "lat" : 12.646
          },
          "ingest_timestamp" : "2022-02-05T10:16:02.692Z",
          "jw" : "Rayong"
        }
      },
      {
        "_index" : "mymap",
        "_type" : "_doc",
        "_id" : "3",
        "_score" : 1.0,
        "_source" : {
          "num" : 75,
          "location" : {
            "lon" : 99.3403,
            "lat" : 10.459
          },
          "ingest_timestamp" : "2022-02-05T10:16:08.783Z",
          "jw" : "Chumphon"
        }
      }
    ]
  }
}
````
