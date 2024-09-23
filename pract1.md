# Практическое занятие №1. Введение, основы работы в командной строке

П.Н. Советов, РТУ МИРЭА

Научиться выполнять простые действия с файлами и каталогами в Linux из командной строки. Сравнить работу в командной строке Windows и Linux.

## Задача 1

Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).
![image](https://github.com/user-attachments/assets/aa7234e4-e981-408c-93d9-76f0e526a9ef)


## Задача 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

```
[root@localhost etc]# cat /etc/protocols ...
142 rohc
141 wesp
140 shim6
139 hip
138 manet
```
![image](https://github.com/user-attachments/assets/a24a16be-b1b1-4fb4-a160-333ce537888f)


## Задача 3

Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!):

```
[root@localhost ~]# ./banner "Hello from RTU MIREA!"
+-----------------------+
| Hello from RTU MIREA! |
+-----------------------+
```
![image](https://github.com/user-attachments/assets/3330892d-320f-4b2c-9622-db9c19719e5d)

Перед отправкой решения проверьте его в ShellCheck на предупреждения.

## Задача 4

Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).

Пример для hello.c:

```
h hello include int main n printf return stdio void world
```
![image](https://github.com/user-attachments/assets/59586a6f-4306-4398-b108-3ff60751db36)

## Задача 5

Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

Например, пусть программа называется reg:

```
./reg banner
```

В результате для banner задаются правильные права доступа и сам banner копируется в /usr/local/bin.
![image](https://github.com/user-attachments/assets/86890267-8a0d-4da0-8379-3a4c46b5c4b1)

## Задача 6

Написать программу для проверки наличия комментария в первой строке файлов с расширением c, js и py.
![image](https://github.com/user-attachments/assets/d615228a-f487-43a8-91fe-221a9172ff0f)

## Задача 7

Написать программу для нахождения файлов-дубликатов (имеющих 1 или более копий содержимого) по заданному пути (и подкаталогам).
![image](https://github.com/user-attachments/assets/ed875651-80d0-4971-85ff-f825912a80a8)

## Задача 8

Написать программу, которая находит все файлы в данном каталоге с расширением, указанным в качестве аргумента и архивирует все эти файлы в архив tar.
![image](https://github.com/user-attachments/assets/b885eae7-00bb-4109-a42d-71cbceca81d8)

## Задача 9

Написать программу, которая заменяет в файле последовательности из 4 пробелов на символ табуляции. Входной и выходной файлы задаются аргументами.
![image](https://github.com/user-attachments/assets/9abc5b16-5850-4bc7-8734-1a2cd58cddd1)

## Задача 10

Написать программу, которая выводит названия всех пустых текстовых файлов в указанной директории. Директория передается в программу параметром. 
![image](https://github.com/user-attachments/assets/e83db9d8-f2ab-4691-a11e-923e459598a3)

## Полезные ссылки

Линукс в браузере: https://bellard.org/jslinux/

ShellCheck: https://www.shellcheck.net/

Разработка CLI-приложений

Общие сведения

https://ru.wikipedia.org/wiki/Интерфейс_командной_строки
https://nullprogram.com/blog/2020/08/01/
https://habr.com/ru/post/150950/

Стандарты

https://www.gnu.org/prep/standards/standards.html#Command_002dLine-Interfaces
https://www.gnu.org/software/libc/manual/html_node/Argument-Syntax.html
https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap12.html

Реализация разбора опций

Питон

https://docs.python.org/3/library/argparse.html#module-argparse
https://click.palletsprojects.com/en/7.x/
