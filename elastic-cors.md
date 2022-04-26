# elastic cors

## file elasticsearch.yml add  

````
http.cors.enabled: true
http.cors.allow-origin: "*"
````

## test

````
curl -H "User-Agent: Mozilla" -H "Origin: http://example.com" -i localhost:9200
````
