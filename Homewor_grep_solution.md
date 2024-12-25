# Homework grep

## Решение

1) Сначала мы ищем строки со словом "ERROR", используя следующую команду:

```
grep "ERROR" server.log
```

В результате на экране появится следующая информация:

```
[ERROR] Unable to connect to database
[ERROR] Application crashed
```

2) Следующим шагом мы ищем сразу жва слова: "WARNING" и "ERROR". Для поиска используем следующую команду:

```
grep -E "ERROR|WARNING" server.log
```

Результат команды будет таким:

```
[WARNING] Disk space is low
[ERROR] Unable to connect to database
[ERROR] Application crashed
```

3) Теперь нужно найти все строки со словом "ERROR", при этом не учитывая регистр. Для такого поиска используем следующую команду:

```
grep -i "error" server.log
```

Результат поиска будет таким:

```
[ERROR] Unable to connect to database
[ERROR] Application crashed
```

Дополнительно) Посчитать, сколько строк, в которых есть слово "ERROR" или "WARNING" можно с помощью такой команды:

```
grep -E "ERROR|WARNING" server.log | wc -l
```

По итогу мы получим число 3.

