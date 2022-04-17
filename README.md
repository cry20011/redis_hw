# Домашнее задание 3 Redis
Установил RedisInsight, и на виртуалке запустил redis-server и кластер (но это чуть позже).
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen10.png)
# Заполнение данными
Строка ~20Мb
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen11.png)


Hset ~20Мb
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen5.png)


Zset ~20Мb
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen7.png)


List ~20Мb
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen8.png)

В среднем 2.5 секунды для 34000 запросов для строки, hset zset и list, вроде неплохо.
В базе получилось:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen12.png)

# Чтение данных
Чтение строки:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen13.png)


Чтение данных из hset, всё очень быстро, даже получить все значения за четверть секунды:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen14.png)


Чтение данных из zset, всё выполняется за несколько миллисекунд:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen15.png)

Чтение данных из list, тоже всё выполняется за несколько миллисекунд:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen16.png)


# Кластер
Развернул кластер из трех нод ([гайд](https://redis.io/docs/manual/scaling/#:~:text=Redis%20Cluster%20provides%20a%20way,are%20not%20able%20to%20communicate)) то есть создал директорию redis-cluster, в ней три директории 7000, 7001, 7002, в каждой создал файл redis.conf и выполнил команду:
```
redis-cli --cluster create 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002
```
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen1.png)


При попытке создать одного мастера и две реплики:
```
:~$ redis-cli --cluster create 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 --cluster-replicas 2
*** ERROR: Invalid configuration for cluster creation.
*** Redis Cluster requires at least 3 master nodes.
*** This is not possible with 3 nodes and 2 replicas per node.
*** At least 9 nodes are required.       
```
То есть я создал три мастера, и в redis-cluster они обязательно должны быть, для n реплик нужно создавать n * (количество мастер-нод).
