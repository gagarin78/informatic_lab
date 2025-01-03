# Лабораторная работа: Использование команды grep в Linux

## 1. Введение

Команда `grep` в Linux — это мощный инструмент для поиска строк в текстовых файлах по заданным шаблонам. Она используется системными администраторами, разработчиками и пользователями для фильтрации данных, анализа логов и многих других задач.

Пример использования:

`grep "hello" file.txt`

Эта команда ищет строки, содержащие слово "hello", в файле file.txt и выводит их в терминал.

Создайте текстовый файл example.txt со следующим содержимым:

```
Hello World
This is a Linux tutorial
grep is a useful tool
Learn Linux commands
```

Используйте команду grep для поиска строк, содержащих слово "Linux".

Ожидаемый результат:

```
This is a Linux tutorial
Learn Linux commands
```

## Основное задание

Вы пришли на собеседование во всем известную биг-тех компанию Undex на позицию системанрго администрартора. Ваша задача написать скрипт для автоматического извлечения из логов тех строк, которые содержат определенные ключевые слова ("ERROR", "WARNING"). В скрипте обязательно должна использоваться команда `grep`.

Ход работы:

- Создайте файл логов server.log со следующим содержимым:

```
[INFO] Server started at 10:00
[WARNING] Disk space is low
[ERROR] Unable to connect to database
[INFO] User logged in
[ERROR] Application crashed
[INFO] Backup completed
```

- Используйте grep для поиска всех строк, содержащих слово "ERROR".

- Найдите строки, содержащие либо "ERROR", либо "WARNING" (подсказка: используйте регулярные выражения).

- Выведите строки с "ERROR", игнорируя регистр букв (например, найдите и "error").

Дополнительно:

Подсчитайте количество строк в файле, содержащих "ERROR" или "WARNING".

## Ресурсы
https://selectel.ru/blog/tutorials/grep-command-in-linux/

https://ru.hexlet.io/courses/cli-basics/lessons/grep/theory_unit
