
# SUM FIELD

````
#
POST /user/_search?size=0
{
  "query": {
    "constant_score": {
      "filter": {
        "match": { "type": "hat" }
      }
    }
  },
  "aggs": {
    "hat_prices": { "sum": { "field": "price" } }
  }
}
````

````
#
POST /user/_search?size=0
{
  "aggs": {
    "sum_age1": {
      "sum": {
        "field": "age"
      }
    }
  }
}
````

````
POST /sales/_search?size=0
{
  "runtime_mappings": {
    "price.weighted": {
      "type": "double",
      "script": """
        double price = doc['price'].value;
        if (doc['promoted'].value) {
          price *= 0.8;
        }
        emit(price);
      """
    }
  },
  "query": {
    "constant_score": {
      "filter": {
        "match": { "type": "hat" }
      }
    }
  },
  "aggs": {
    "hat_prices": {
      "sum": {
        "field": "price.weighted"
      }
    }
  }
}
````

