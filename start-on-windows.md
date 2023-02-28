# start on windows

## 1-START-ELASTIC.bat

```bat
@ECHO ON
REM START D:\app\elasticsearch-7.14.1\bin\elasticsearch.bat
D:
CD D:\app\elasticsearch-7.14.1\
START .\bin\elasticsearch.bat
```

## 2-START-KIBANA.bat

```bat
@ECHO ON 
REM START D:\app\kibana-7.14.1-windows-x86_64\bin\kibana.bat
D:
CD D:\app\kibana-7.14.1-windows-x86_64\
START .\bin\kibana.bat
```

## 3-START-LOGSTASH.bat

```bat
@ECHO ON
REM START D:\app\logstash-7.14.1\bin\logstash.bat -f D:\app\logstash-7.14.1\config\syslog.conf
D:
CD D:\app\logstash-7.14.1\
START .\bin\logstash.bat -f .\config\rsyslog.conf
```
