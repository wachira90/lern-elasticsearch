# logstash export csv

````
input {
	 elasticsearch {
	    hosts => "localhost:9200"
	    index => "index-we-are-reading-froml"
	    query => '
	  {"query": {
	   .. 
	#Insert your Elasticsearch query here
	        }
	      }
	    }
	}}'
	  }
	}
	output {
	  csv {
	# This is the field that you would like to output in CSV format.
	# The field needs to be one of the fields shown in the output when you run your
	# Elasticsearch query
		 fields => ["field1", "field2", "field3", "field4","field5"]
        # This is where we store output. We can use several files to store our output
        # by using a timestamp to determine the filename where to store output.    
	path => "/tmp/csv-export.csv"
	  }
	}
````
