# Практическое занятие №2. Менеджеры пакетов

П.Н. Советов, РТУ МИРЭА

Разобраться, что представляет собой менеджер пакетов, как устроен пакет, как читать версии стандарта semver. Привести примеры программ, в которых имеется встроенный пакетный менеджер.

## Задача 1

Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?
![image](https://github.com/user-attachments/assets/d1f6e59b-1483-40cd-b90d-d5d68d85d2bd)
![image](https://github.com/user-attachments/assets/c6c731bc-8ec5-4b1f-a01d-e43054036382)


## Задача 2

Вывести служебную информацию о пакете express (JavaScript). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?
![image](https://github.com/user-attachments/assets/8b183ee5-f60f-4201-9ed3-4ed1dfdfefc4)
![image](https://github.com/user-attachments/assets/54061d31-8f39-49ea-8d59-0c196c193727)


## Задача 3

Сформировать graphviz-код и получить изображения зависимостей matplotlib и express.

![dependencies](https://github.com/user-attachments/assets/7de1e4f2-71be-48bd-a05e-a72fd1d5eb1f)

![image](https://github.com/user-attachments/assets/8ef364f4-8948-4c87-a21e-bcc0c2224432)
![image](https://github.com/user-attachments/assets/e892a556-b9df-449e-a0b3-1b488f112a2e)


## Задача 4

**Следующие задачи можно решать с помощью инструментов на выбор:**

* Решатель задачи удовлетворения ограничениям (MiniZinc).
* SAT-решатель (MiniSAT).
* SMT-решатель (Z3).

Изучить основы программирования в ограничениях. Установить MiniZinc, разобраться с основами его синтаксиса и работы в IDE.

Решить на MiniZinc задачу о счастливых билетах. Добавить ограничение на то, что все цифры билета должны быть различными (подсказка: используйте all_different). Найти минимальное решение для суммы 3 цифр.

![image](https://github.com/user-attachments/assets/acd3cda9-7777-40aa-a217-19986b42f3c7)

## Задача 5

Решить на MiniZinc задачу о зависимостях пакетов для рисунка, приведенного ниже.

![](images/pubgrub.png)

![image](https://github.com/user-attachments/assets/a339a26b-ee99-4472-a062-4b0ffd9c8ed7)


## Задача 6

Решить на MiniZinc задачу о зависимостях пакетов для следующих данных:

```
root 1.0.0 зависит от foo ^1.0.0 и target ^2.0.0.
foo 1.1.0 зависит от left ^1.0.0 и right ^1.0.0.
foo 1.0.0 не имеет зависимостей.
left 1.0.0 зависит от shared >=1.0.0.
right 1.0.0 зависит от shared <2.0.0.
shared 2.0.0 не имеет зависимостей.
shared 1.0.0 зависит от target ^1.0.0.
target 2.0.0 и 1.0.0 не имеют зависимостей.
```
![image](https://github.com/user-attachments/assets/b9f976ab-39f9-4940-b218-9c08fa3634fa)

![image](https://github.com/user-attachments/assets/cb9564ed-2c20-4ebb-a29f-573ec8eda78d)

![image](https://github.com/user-attachments/assets/1c5b774c-2f7b-4329-af34-87b3637505a6)



## Задача 7

Представить задачу о зависимостях пакетов в общей форме. Здесь необходимо действовать аналогично реальному менеджеру пакетов. То есть получить описание пакета, а также его зависимости в виде структуры данных. Например, в виде словаря. В предыдущих задачах зависимости были явно заданы в системе ограничений. Теперь же систему ограничений надо построить автоматически, по метаданным.

# Пример структуры данных с зависимостями и версиями
packages = {
    "root": {"dependencies": ["foo", "target"], "version": None},
    "foo": {"dependencies": ["left", "right"], "version": None},
    "left": {"dependencies": ["shared>=1.0.0"], "version": None},
    "right": {"dependencies": ["shared<2.0.0"], "version": None},
    "shared": {"dependencies": [], "version": None},
    "target": {"dependencies": [], "version": None},
}

def generate_minizinc_code(packages):
    package_names = ', '.join(packages.keys())
    # Генерация массива установленных пакетов
    minizinc_code = f"enum PACKAGES = {{{package_names}}};\n"
    minizinc_code += "array[PACKAGES] of var 0..1: installed;\n\n"
    # Добавляем условие для root
    minizinc_code += "constraint installed[root] == 1;\n"
    # Генерация ограничений
    for package, details in packages.items():
        dependencies = details["dependencies"]
        if dependencies:
            dep_constraints = []
            for dep in dependencies:
                if '>' in dep or '<' in dep or '=' in dep:
                    dep_name = dep.split('>=')[0].split('<')[0].split('=')[0]
                    dep_constraints.append(f"installed[{dep_name}] == 1")
                else:
                    dep_constraints.append(f"installed[{dep}] == 1")
            constraint = "constraint installed[{}] == 1 -> ({});\n".format(
                package, ' /\\ '.join(dep_constraints)
            )
            minizinc_code += constraint
    minizinc_code += "\nsolve minimize sum(installed);\n"
    minizinc_code += 'output ["Installed packages: ", show(installed)];\n'
    return minizinc_code


# Генерация и вывод MiniZinc кода
minizinc_code = generate_minizinc_code(packages)
print(minizinc_code)

## Полезные ссылки

Semver: https://devhints.io/semver

Удовлетворение ограничений и программирование в ограничениях: http://intsys.msu.ru/magazine/archive/v15(1-4)/shcherbina-053-170.pdf

Скачать MiniZinc: https://www.minizinc.org/software.html

Документация на MiniZinc: https://www.minizinc.org/doc-2.5.5/en/part_2_tutorial.html

Задача о счастливых билетах: https://ru.wikipedia.org/wiki/%D0%A1%D1%87%D0%B0%D1%81%D1%82%D0%BB%D0%B8%D0%B2%D1%8B%D0%B9_%D0%B1%D0%B8%D0%BB%D0%B5%D1%82
