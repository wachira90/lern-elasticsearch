# user manage

## create user

```
POST _security/user/sam
{
  "password" : "xxxx",
  "roles" : [ "superuser"],
  "full_name" : "Sam John",
  "email" : "sam@example.com"
}
```

## get info

```
GET _security/user/logstash_system

GET _security/user/elastic

GET _security/user/

GET _security/user/sam
```

## enable and disable

```
PUT _security/user/sam/_disable

PUT _security/user/sam/_enable
```
