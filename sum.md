
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
