# add security

test on version 7.14.1 windows

## add system variable

````
CLASSPATH => C:\Program Files\Java\jdk1.8.0_251\jre\lib
JAVA_HOME => C:\Program Files\Java\jdk1.8.0_251
ES_JAVA_HOME => C:\Program Files\Java\jdk1.8.0_251
ES_PATH_CONF => D:\elk\elasticsearch-7.14.1\config
````

## add in file `elasticsearch.yml`

````
cluster.name: nameexample
network.host: localhost
http.port: 9200
discovery.type: single-node
xpack.license.self_generated.type: basic

xpack.security.enabled: true 
````

## start

````
.\bin\elasticsearch.bat
````

## gen password

````
.\bin\elasticsearch-setup-passwords.bat auto
````

## output

````
Changed password for user apm_system
PASSWORD apm_system = o8TgdPzXHvZPNoFG2hMW

//USE HERE IN kibana.yml
Changed password for user kibana_system
PASSWORD kibana_system = NsUym5ib0magOx4stHgK

Changed password for user kibana
PASSWORD kibana = NsUym5ib0magOx4stHgK

Changed password for user logstash_system
PASSWORD logstash_system = uvkjPFxmiCrgXZMNxlNo

Changed password for user beats_system
PASSWORD beats_system = KBdiov4YlTVbNZo0jnbM

Changed password for user remote_monitoring_user
PASSWORD remote_monitoring_user = WQNeiu1d7SVP8uXTRD6q

//FOR LOGIN DASH BOARD KIBANA
Changed password for user elastic
PASSWORD elastic = r13IrHd29XPX6GkW7hNZ
````


## HTTP
````
GET http://localhost:9200/mymap/_search
Content-Type: application/json; charset=utf-8
Authorization: Basic ZWxhc3RpYzpyMTNJckhkMjlYUFg2R2tXN2hOWg==

{
  "query": {
    "match_all": {}
  }
}


GET http://localhost:9200/_security/user/elastic
Content-Type: application/json; charset=utf-8
Authorization: Basic ZWxhc3RpYzpyMTNJckhkMjlYUFg2R2tXN2hOWg==


curl --user elastic:r13IrHd29XPX6GkW7hNZ -XGET "http://localhost:9200/mymap/_search"


````
base64(USERNAME:PASSWORD)

BASE64 : https://www.base64encode.org/




