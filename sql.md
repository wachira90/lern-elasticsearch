# sql command

````
#
POST _sql?format=json
{
  "query": """
  SELECT * FROM "user" WHERE "age" < 30
  """
}

#
POST _sql?format=csv
{
  "query": """
  SELECT * FROM "user"
  """
}

#
POST _sql?format=txt
{
  "query": """
  SELECT * FROM "user"
  """
}
````
