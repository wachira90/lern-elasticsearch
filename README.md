# lern-elasticsearch
lern-elasticsearch

## search
````
GET /bemislog1-*/_search?pretty=true
{
  "query": {
    "match": {
      "message": "/graphql"
    }
  }
}
````

## python

````
import requests
import json

def search(uri, term):
    """Simple Elasticsearch Query"""
    query = json.dumps({
       "timeout": "5s",
        "query": {
            "match": {
                "message": term
            }
        }
    })
    headers = {'content-type': 'application/json'}
    response = requests.get(uri, data=query, headers=headers)
    results = json.loads(response.text)
    return results

search('http://172.16.1.5:9200/bemislog1-*/_search?pretty=true','.php')
````
