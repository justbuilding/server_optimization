# 服务器性能优化

## 1.压力测试

>  1.ab压测工具

​         安装：yum install httpd-tools

​         命令：ab -n 10 -c 10 http://baidu.com/

​         解说: -n表示总的请求为10  -c表示并发数为10 

​         注意：网址后的斜杠不能丢

```
[root@localhost ~]# ab -n 10 -c 10 http://baidu.com/
This is ApacheBench, Version 2.3 <$Revision: 1430300 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking baidu.com (be patient).....done


Server Software:        
Server Hostname:        baidu.com
Server Port:            80

Document Path:          /
Document Length:        0 bytes

Concurrency Level:      10 
                        并发量
Time taken for tests:   1.015 seconds
                        花费的总时间
Complete requests:      10
                        请求量
Failed requests:        6
   (Connect: 0, Receive: 0, Length: 6, Exceptions: 0)
Write errors:           0
Total transferred:      2286 bytes
                        传输的总流量
HTML transferred:       486 bytes
                        传输量
Requests per second:    9.85 [#/sec] (mean)
                        每秒事务数，即每秒处理的请求数
Time per request:       1014.894 [ms] (mean)    
                        客户端单个请求所用的时间，即平均响应时间
Time per request:       101.489 [ms] (mean, across all concurrent requests)
                        服务端处理每个请求的时间，不包括网络传输时间等
Transfer rate:          2.20 [Kbytes/sec] received
                        服务端处理请求的时间，不包括网络传输时间等

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:       52   54   1.1     54      56
Processing:    56  114 118.1     58     341
Waiting:        0   34  29.7     57      59
Total:        110  168 118.7    112     396

Percentage of the requests served within a certain time (ms)
  50%    112                      50%的请求响应时间小于112ms
  66%    112
  75%    115
  80%    390
  90%    396
  95%    396
  98%    396
  99%    396
 100%    396 (longest request)    最长响应时间396ms
```

###### 测试静态接口  ab -n 10 -c 10 localhost/test.html

###### 测试动态接口  ab -n 10 -c 10 localhost/test.php