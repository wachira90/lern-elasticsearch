# add geo 

## command 
````
PUT mymap
{
  "mappings": {
    "properties": {
      "location": {
        "type": "geo_point"
      }
    }
  }
}
````

## output
````
PUT my-index-000001/_doc/1
{
  "text": "Geopoint as an object",
  "location": { 
    "lat": 41.12,
    "lon": -71.34
  }
}
````
