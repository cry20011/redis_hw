# Домашнее задание 3 Redis
Установил RedisInsight, и на виртуалке запустил redis-server и создал кластер из трех нод.
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen1.png)
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


Чтение данных из hset, всё выполняется за несколько миллисекунд:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen14.png)


Чтение данных из zset, тоже всё выполняется за несколько миллисекунд:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen15.png)

Чтение данных из list, тоже всё выполняется за несколько миллисекунд, кроме:
![](https://github.com/cry20011/redis_hw/raw/main/screens/screen15.png)
