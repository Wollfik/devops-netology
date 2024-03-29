# Домашнее задание к занятию 6. «Troubleshooting»

## Задача 1

Перед выполнением задания ознакомьтесь с документацией по [администрированию MongoDB](https://docs.mongodb.com/manual/administration/).

Пользователь (разработчик) написал в канал поддержки, что у него уже 3 минуты происходит CRUD-операция в MongoDB и её 
нужно прервать. 

Вы как инженер поддержки решили произвести эту операцию:

- напишите список операций, которые вы будете производить для остановки запроса пользователя;
- предложите вариант решения проблемы с долгими (зависающими) запросами в MongoDB.

_**Для определения операций по длительности больше 3 минут, сделаю запрос: `db.currentOp({ "active" : true, "secs_running" : { "$gt" : 180 }})`**_

_**И дальше завершу операцию запросом `db.killOp(<opid of the query to kill>)`.**_

**_Для решения проблемы в текущей ситуации сложно что-то предложить, так как не совсем понятна причина зависания. Как один из вариантов ускорения Read запросов, могу предложить создать индекс по частой и большой таблице._**

## Задача 2

Перед выполнением задания познакомьтесь с документацией по [Redis latency troobleshooting](https://redis.io/topics/latency).

Вы запустили инстанс Redis для использования совместно с сервисом, который использует механизм TTL. 
Причём отношение количества записанных key-value-значений к количеству истёкших значений есть величина постоянная и
увеличивается пропорционально количеству реплик сервиса. 

При масштабировании сервиса до N реплик вы увидели, что:

- сначала происходит рост отношения записанных значений к истекшим,
- Redis блокирует операции записи.

Как вы думаете, в чём может быть проблема?

_**Скорее всего, проблема заключается в том, что накапливается большое количество просроченных ключей (>25%), при очистке которых, происходит блокировка операции записи.**_
 
## Задача 3

Вы подняли базу данных MySQL для использования в гис-системе. При росте количества записей в таблицах базы
пользователи начали жаловаться на ошибки вида:
```python
InterfaceError: (InterfaceError) 2013: Lost connection to MySQL server during query u'SELECT..... '
```

Как вы думаете, почему это начало происходить и как локализовать проблему?

_**Локализовать проблему можно просмотром логов (с ключом --log-error-verbosity=3).**_

_**Из возможных причин можно отметить:**_
- _**раз проблема началась при росте количества записей в таблицах, то, вероятнее всего, ошибка возникает большого ответа;**_
- _**либо, совпадение, начались сетевые проблемы.**_

Какие пути решения этой проблемы вы можете предложить?

_**Всё зависит от ситуации в логах, но что можно предложить: увеличение значения настройки max_allowed_packet, проверка состояния сети и DNS, попросить добавить ограничения в запросы, добавить индексы.**_

## Задача 4

Вы решили перевести гис-систему из задачи 3 на PostgreSQL, так как прочитали в документации, что эта СУБД работает с 
большим объёмом данных лучше, чем MySQL.

После запуска пользователи начали жаловаться, что СУБД время от времени становится недоступной. В dmesg вы видите, что:

`postmaster invoked oom-killer`

Как вы думаете, что происходит?

**_Какой-то из процессов запрашивает память больше, чем свободно, приходит OOM killer и убивает postmaster так как он потребляет больше всего памяти._**

Как бы вы решили эту проблему?

**_Найти виновника большого потребления памяти и отталкиваться от этого. Также можно постараться уменьшить потребляемую память postmaster, через добавление индексов._**

**_Также можно немного изменить настройки OOM Killer'a: `sysctl -w vm.overcommit_memory=2`. (это в последнюю очередь) И самого ядра s`ysctl -w kernel.shmmax=17179869184 ; sysctl -w kernel.shmall=4194304`._**
**_И в postgresql.conf можно указать значения побольше для параметров `shared_buffers` (25% или еще лучше 40% от общего RAM), `work_mem` и `hash_mem_multiplier`. С последними двумя главное не перебрать._**
