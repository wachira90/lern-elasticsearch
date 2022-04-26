# CREATE USER TOKEN

## AUTO GENERATE TOKEN NAME

````
POST http://localhost:9200/_security/service/elastic/fleet-server/credential/token
Content-Type: application/json; charset=utf-8
Authorization: Basic ZWxhc3RpYzpyMTNJckhkMjlYUFg2R2tXN2hOWg==
````

## CREATE USER TOKEN WITH NAME

````
POST http://localhost:9200/_security/service/elastic/fleet-server/credential/token/token1
Content-Type: application/json; charset=utf-8
Authorization: Basic ZWxhc3RpYzpyMTNJckhkMjlYUFg2R2tXN2hOWg==
````

## DELETE USER TOKEN

````
DELETE http://localhost:9200/_security/service/elastic/fleet-server/credential/token/token1
Content-Type: application/json; charset=utf-8
Authorization: Basic ZWxhc3RpYzpyMTNJckhkMjlYUFg2R2tXN2hOWg==
````

## WHEN CREATE TOKEN USE WITH 'Authorization Bearer'

````
Authorization: Bearer AAEAAWVsYXN0aWMvZmxlZXQtc2VydmVyL3Rva2VuMjpZRVJ6WlBnZVNyNlFvWDdpaVQwa3R3
````
