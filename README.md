# nginx_kafka_redis_module

***
## 模块介绍

`nginx_kafka_redis_module`作为Nginx模块，其作用为截获HTTP的POST请求后根据参数查询Redis库，查询后将HTTP请求的POST内容写入到Kafka中。


## 依赖

该模块需依赖[librdkafka](https://github.com/edenhill/librdkafka)库（C\C++的Kafka接口库）以及[hiredis](https://github.com/redis/hiredis)库（C的Redis接口库）。

## Nginx conf配置

	http {
    		kafka_broker_list 192.168.76.232:9092 192.168.76.233:9092 ; # kafka的broker配置列表

 		    server {
        	listen       8080;
        	server_name  192.168.76.223;

  	        location = /topic { 
   		         redis_host 127.0.0.1; #redis地址
          	     redis_flag on;	#是否开启redis查询
          	     kafka_topic kafkatopic;  #kafka的topic名
        		}
   		    }
  		 }


