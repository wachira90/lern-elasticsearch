# logstash load from db

````
input {
    jdbc {
        jdbc_connection_string => "jdbc:redshift://xxx.us-west-2.redshift.amazonaws.com:5439/xxx"
        jdbc_user => "xxx"
        jdbc_password => "xxx"
        jdbc_validate_connection => true
        jdbc_driver_library => "/mnt/logstash-6.0.0/RedshiftJDBC42-1.2.10.1009.jar"
        jdbc_driver_class => "com.amazon.redshift.jdbc42.Driver"
        schedule => "0 1/12 * * *" #01:00,13:00, tried from https://crontab.guru/#0_1/12_*_*_*
        # 0 */12 * * * # Every twelve hours at minute 0 of the hour.
        # 0 1,12 * * * # Run at one and twelve hours at minute 0.
        statement_filepath => "conf/log_event_query.sql"
        use_column_value => true
        tracking_column => dw_insert_dt
        last_run_metadata_path => "metadata/logstash_jdbc_last_run_log_event"
    }
}
output {
    elasticsearch {
        index => "logs-ics_%{+dd_MM_YYYY}"
        document_type => "log_event"
        document_id => "%{log_entry_id}"
        hosts => [ "x.x.x.x:xxxx" ]
    }
}
````

