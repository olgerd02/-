# Практическое занятие №7. Генераторы документации

П.Н. Советов, РТУ МИРЭА

## Задача 1

Реализовать с помощью математического языка LaTeX нижеприведенную формулу:

![image](https://github.com/user-attachments/assets/4c234fc0-b64d-43c8-8697-33b7f01dec91)
```
\documentclass{article}
\usepackage[T2A]{fontenc} % Поддержка кириллицы
\usepackage[utf8]{inputenc} % Кодировка UTF-8
\usepackage[russian]{babel} % Подключение русского языка
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{graphicx}

\begin{document}

\begin{center}
    \textbf{Петрова Ольга Петровна}
\end{center}

\[
\int_{x}^{\infty} \frac{dt}{t(t^{2}-1)\log t} = \int_{x}^{\infty} \frac{1}{t\log t} \left( \sum_{m} t^{-2m} \right) dt = \sum_{m} \int_{x}^{\infty} \frac{t^{-2m}}{t\log t} dt \quad = -\sum_{m} \mathrm{li}(x^{-2m})
\]

\end{document}
```
Прислать код на LaTeX и картинку-результат, где, помимо формулы, будет указано ФИО студента.

## Задача 2

На языке PlantUML реализовать диаграмму на рисунке ниже. Прислать текст на PlantUML и картинку-результат, в которой ФИО студента заменены Вашими собственными.
Обратите внимание на оформление, желательно придерживаться именно его, то есть без стандартного желтого цвета и проч. Чтобы много не писать используйте псевдонимы с помощью ключевого слова "as".

```
@startuml

' Убираем стандартный желтый цвет
skinparam backgroundColor white
skinparam sequenceArrowColor black
skinparam actorBorderColor black
skinparam participantBorderColor black
skinparam noteBackgroundColor white
skinparam noteBorderColor black

' Псевдонимы
actor "Студент Петрова О.П." as Student
actor "Преподаватель" as Teacher
participant "Piazza" as Piazza

' Диаграмма
Student -> Piazza: Публикация задачи
Piazza -> Teacher: Задача опубликована
Teacher -> Piazza: Поиск задач
Piazza -> Teacher: Получение задачи
Teacher -> Piazza: Публикация решения
Piazza -> Student: Решение опубликовано
Student -> Piazza: Поиск решений
Piazza -> Student: Решение найдено
Student -> Piazza: Публикация оценки
Piazza -> Teacher: Оценка опубликована
Teacher -> Piazza: Проверка оценки
Piazza -> Teacher: Оценка получена

@enduml
```
![bLJBIiD05DtFLmpTkD8FS25LVq3G7nZJmGPhefCfWgi-e0eLt0ZkhE8Fn4UqBzDVkFD7dfc4ccAgba0ouPvxpptdX5GZBPHkdZGOM-FqHCyqD2sAAQ4fDstJmV6JtYWsBPm_JPz6dDvHdPYEUp4zUg74T5Xqx0UdGeaJVYYyuoCLDeFQRjW85J-l-reMwf4yQyh0azjAXUSPvB21dW9](https://github.com/user-attachments/assets/c3cc8abe-dae6-44ba-a167-49e8ec817374)


Используйте [онлайн-редактор](https://plantuml-editor.kkeisuke.com/).


## Задача 3

Описать какой-либо алгоритм сортировки с помощью noweb. Язык реализации не важен. Прислать nw-файл, pdf-файл и файл с исходным кодом. В начале pdf-файла должно быть указано ваше авторство. Добавьте, например, где-то в своем тексте сноску: \footnote{Разработал Фамилия И.О.}
Дополнительное задание: сравните "грамотное программирование" с Jupyter-блокнотами (см. https://github.com/norvig/pytudes/blob/master/ipynb/BASIC.ipynb), опишите сходные черты, различия, перспективы того и другого.

## Задача 4

Выбрать программный проект из нескольких файлов (лучше свой собственный), состоящий из нескольких файлов. Получить для него документацию в Doxygen. Язык реализации не важен. Должны быть сгенерированы: описания классов и функций, диаграммы наследования, диаграммы графа вызовов функции. Прислать pdf-файл с документацией (см. latex/make.bat), в котором будет указано ваше авторство. Необходимо добиться корректного вывода русского текста.
 
## Задача 5

Выбрать программный проект на Python (лучше свой собственный), состоящий из нескольких файлов. Получить для него документацию в Doxygen. Должны быть сформированы: руководство пользователя и руководство программиста. Руководство программиста должно содержать описание API, полученное с использованием расширения autodoc. Для каждого из модулей должна присутствовать диаграмма наследования и подробное описание классов и функций (назначение, описание параметров и возвращаемых значений), извлеченных из docstring. Прислать pdf-файл с документацией, в котором будет указано ваше авторство и весь авторский текст приведен на русском языке.

## Полезные ссылки

**LaTeX**

http://grammarware.net/text/syutkin/TextInLaTeX.pdf

https://grammarware.net/text/syutkin/MathInLaTeX.pdf

https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes

https://www.overleaf.com/learn/latex/XeLaTeX

**Noweb**

https://www.pbr-book.org/3ed-2018/Introduction/Literate_Programming

https://www.cs.tufts.edu/~nr/noweb/

**Doxygen**

https://www.doxygen.nl/index.html

https://habr.com/ru/post/252101/

**Sphinx**

https://www.sphinx-doc.org/en/master/

https://sphinx-ru.readthedocs.io/ru/latest/index.html

https://breathe.readthedocs.io/en/latest/


**PlantUML**

https://plantuml.com/ru/

https://pdf.plantuml.net/PlantUML_Language_Reference_Guide_ru.pdf

**Mermaid**

https://mermaid.js.org/

https://mermaid.live/edit
