# Лабораторная работа №3
## Задание 1 - Автоматизация проверки формата файлов при коммите
Предположим, у вас есть задача автоматизировать проверку формата файлов при коммите с использованием Git Hooks.

Перед каждым коммитом необходимо автоматически проверять, чтобы все .txt файлы в репозитории соответствовали определенному формату.

Создайте bash-скрипт, который будет выполнять проверку того, что коммитится файл формата .txt и в файле присутствует какой-то текст (например, в конце файла есть подпись автора, неважно как она выглядит, главное чтобы была какая-нибудь проверка содержимого файла). Далее поместите этот скрипт в нужную папку и проверьте, что перед каждым коммитом проходит проверка, например, добавьте вывод о результате проверки в консоль. За этот функционал отвечает Git Hooks, там сказазно как автоматизировать такую проверку.

## Решение задания 1
1. Сначала нужно клонировать нужный нам репозиторий. Для этого в терминал вводим команду `git clone <your_repository_url>.git`
2. Затем переходим в каталог репозитория
3. После этого нужно перейти в каталог хуков. Чтобы сделать этот переход используем команду `cd .git/hooks`. В этом каталоге создаем файл pre-commit, в котром вводим следующий код:
   ```
   #!/bin/bash

   # Флаг для отслеживания ошибок
   has_errors=false

   # Получаем список файлов, которые будут закоммичены
   files_to_check=$(git diff --cached --name-only --diff-filter=ACMR | grep '\.txt$')

   # Если нет .txt файлов, завершить хук
   if [[ -z "$files_to_check" ]]; then
   echo "No .txt files to check."
   exit 0
   fi

   # Проверяем каждый .txt файл
   for file in $files_to_check; do
   # Проверяем, существует ли файл (может быть удален перед коммитом)
   if [[ ! -f "$file" ]]; then
    echo "Warning: $file does not exist."
    continue
   fi

   # Проверяем, содержит ли файл подпись (например, строку "Author:" в конце)
   if ! grep -q "Author:" "$file"; then
     echo "Error: $file does not contain 'Author:' signature."
     has_errors=true
   fi
   done

   # Если были ошибки, отменяем коммит
   if $has_errors; then
   echo "Commit aborted due to errors in .txt files."
   exit 1
   fi

   echo "All .txt files passed the check."
   exit 0
   ```
4. Следующим шагом является ввод команды `chmod +x pre-commit`, чтобы скрипт стал исполняемым.
5. 