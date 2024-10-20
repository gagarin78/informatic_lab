# Лабораторная работа №2
## Задание
На основе изученного материала лабораторной работы, лекций (2 и 3), дополнительных источников напишите скрипт, который на вход принимает IPv4-адрес в десятичном формате, а на выходе обеспечивает данный IP-адрес в двоичном формате.

Пример входных данных:

`192.168.10.1`

Пример выходныx данных:

`11000000.10101000.00001010.00000001`

## Листинг кода
```
#!/bin/bash
IP=$1
IFS='.' read oct1 oct2 oct3 oct4 <<< "$IP"
to_binary() {
  echo "obase=2; $1" | bc
}

oct1=$(to_binary $oct1)
oct2=$(to_binary $oct2)
oct3=$(to_binary $oct3)
oct4=$(to_binary $oct4)

printf "%08d.%08d.%08d.%08d\n" $oct1 $oct2 $oct3 $oct4
```

## Объяснение работы кода
Задаем shebang, который указывает, что скрипт нужно выполнять с помощью интерпретатора Bash.

`#!/bin/bash`

Считываем один, введеный, аргумент.

`IP=$1"`

Разделяем полученную строку по симолу точки.

`IFS='.' read oct1 oct2 oct3 oct4 <<< "$IP"`

Прописываем функцию, которая будет переводить входные данные в двоичную систему счисления.

```
to_binary() {
  echo "obase=2; $1" | bc
}
```

 К каждой переменной oct1, oct2, oct3 и oct4 применяем функцию перевода в двоичную систему счисления и переприсваиваем их.

 ```
oct1=$(to_binary $oct1)
oct2=$(to_binary $oct2)
oct3=$(to_binary $oct3)
oct4=$(to_binary $oct4)
```

Дополняем переменные до восьми знаков, разделяем их точками и записываем в одну строку.

`printf "%08d.%08d.%08d.%08d\n" $oct1 $oct2 $oct3 $oct4`