# Курс: Информатика
#computer_science #python #note 
# Практическое занятие №5. "Погружение в Python"
```python
import this
The Zen of Python, by Tim Peters
<BLANKLINE>
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```
> Встроенные функции в [python](https://docs.python.org/3/library/functions.html)

- [[#Списки (List)]]
	- [[#Создание списка]]
	- [[#Операции с списком]]
	- [[#Итерация списка и поиск]]
	- [[#Удаление списка]]
	- [[#Сортировка списка]]
	- [[#Списки и математика]]
- [[#Управление файлами]]
	- [[#Ввод и вывод файлов]]
	- [[#Распространенные идиомы чтения данных файла|Распространенные идиомы чтения данных файла]]
	- [[#Распространенные идиомы записи в файл]]
- [[#Функции]]
	- [[#Пользовательские функции]]
	- [[#Библиотечные функции]]
	- [[#Ошибки и исключения]]
	- [[#Перехват и обработка исключений]]
	- [[#Вызов исключений]]
- [[#Контейнеры]]
	- [[#Обзор]]
	- [[#Списки как контейнер]]
	- [[#Построение списка]]
	- [[#Словари как контейнер]]
	- [[#Создание словарей]]
	- [[#Поиск по словарю]]
	- [[#Составные ключи]]
	- [[#Наборы]]
- [[#Форматирование]]
	- [[#Форматирование строк]]
	- [[#Коды форматирования]]
	- [[#Форматирование словаря]]
	- [[#Метод `format()`]]
	- [[#Форматирование в стиле C]]
- [[#Последовательности]]
	- [[#Типы данных последовательности]]
	- [[#Нарезка]]
	- [[#Переназначение фрагмента]]
	- [[#Сокращение последовательности]]
	- [[#Итерация по последовательности]]
	- [[#Оператор разрыва]]
	- [[#Оператор продолжения]]
	- [[#Цикл по целым числам]]
	- [[#функция перечисления]]
	- [[#Циклы и кортежей]]
	- [[#Функция zip()]]
- [[#Взаимодействие со списками]]
	- [[#Создание новых списков]]
	- [[#Фильтрация]]
	- [[#Случаи использования]]
	- [[#Общий синтаксис]]
	- [[#Исторический экскурс]]
- [[#Объекты]]
	- [[#|Assignment]]
	- [[#Пример назначения]]
	- [[#Переназначение значений]]
	- [[#Идентификация и ссылки]]
	- [[#Мелкие копии]]
	- [[#Глубокие копии]]
	- [[#Имена, значения, типы]]
	- [[#Проверка типа]]
- [[#Все является объектом]]

### Списки (List)

В этом разделе представлены списки — основной тип Python для хранения упорядоченной коллекции значений.

#### Создание списка

Используйте квадратные скобки для определения литерала списка:

```python
names = [ 'Elwood', 'Jake', 'Curtis' ]
nums = [ 39, 38, 42, 65, 111]
```

Иногда списки создаются другими методами. Например, строку можно разделить на список с помощью метода `split()`:

```python
>>> line = 'GOOG,100,490.10'
>>> row = line.split(',')
>>> row
['GOOG', '100', '490.10']
>>>
```

#### Операции с списком

Списки могут содержать элементы любого типа. Добавьте новый элемент с помощью `append()`:

```python
names.append('Murphy')    # Adds at end
names.insert(2, 'Aretha') # Inserts in middle
```

Используйте `+` для объединения списков:

```python
s = [1, 2, 3]
t = ['a', 'b']
s + t           # [1, 2, 3, 'a', 'b']
```

Списки индексируются целыми числами. Начиная с 0.

```python
names = [ 'Elwood', 'Jake', 'Curtis' ]

names[0]  # 'Elwood'
names[1]  # 'Jake'
names[2]  # 'Curtis'
```

Отрицательные индексы отсчитываются с конца.

```python
names[-1] # 'Curtis'
```

Вы можете изменить любой элемент в списке.

```python
names[1] = 'Joliet Jake'
names                     # [ 'Elwood', 'Joliet Jake', 'Curtis' ]
```

Длина списка.

```python
names = ['Elwood','Jake','Curtis']
len(names)  # 3
```

Тест на членство (`in`, `not in`).

```python
'Elwood' in names       # True
'Britney' not in names  # True
```

Репликация (`s*n`).

```python
s = [1, 2, 3]
s * 3   # [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

#### Итерация списка и поиск

Используйте `for` для перебора содержимого списка.

```python
for name in names:
    # use name
    # e.g. print(name)
    ...
```

Это похоже на оператор `foreach` из других языков программирования.
Чтобы быстро найти положение чего-либо, используйте `index()`.

```python
names = ['Elwood','Jake','Curtis']
names.index('Curtis')   # 2
```

Если элемент присутствует более одного раза, `index()` вернет индекс первого вхождения.
Если элемент не найден, будет выдано [исключение](https://docs.python.org/3/library/exceptions.html) `ValueError`.

#### Удаление списка

Вы можете удалять элементы либо по значению элемента, либо по индексу:

```python
# Using the value
names.remove('Curtis')

# Using the index
del names[1]
```

Удаление предмета не создает дыру. Другие предметы будут двигаться вниз чтобы заполнить освободившееся место. Если имеется более одного появления элемент `remove()` удалит только первое вхождение.

#### Сортировка списка

Сортировка списка

```python
s = [10, 1, 7, 3]
s.sort()                    # [1, 3, 7, 10]

# Reverse order
s = [10, 1, 7, 3]
s.sort(reverse=True)        # [10, 7, 3, 1]

# It works with any ordered data
s = ['foo', 'bar', 'spam']
s.sort()                    # ['bar', 'foo', 'spam']
```

Используйте `sorted()`, если вместо этого вы хотите создать новый список:

```python
t = sorted(s)               # s unchanged, t holds sorted values
```

#### Списки и математика

>*списки не предназначены для математических операций.*

```python
>>> nums = [1, 2, 3, 4, 5]
>>> nums * 2
[1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
>>> nums + [10, 11, 12, 13, 14]
[1, 2, 3, 4, 5, 10, 11, 12, 13, 14]
```

В частности, списки не представляют векторы/матрицы, как в MATLAB, Octave, R и т. д. Однако есть несколько пакетов, которые помогут вам в этом (например, [numpy](https://numpy.org)).

### Управление файлами

Большинству программ необходимо откуда-то считывать вводимые данные. В этом разделе обсуждается доступ к файлам.

#### Ввод и вывод файлов

Можете использовать `bash` скрипт для созданния тестовых файлов.
```bash
 #!/bin/bash  
 # generate random content using base64 
 rand_content=$(cat /dev/urandom | base64 | head -c 100) 
 # write random content to foo.txt and bat.txt  
 echo  "$rand_content" > foo.txt echo  "$rand_content" > bat.txt
 rand_content=$(cat /dev/urandom | base64 | head -c 100)
 "$rand_content" > bar.txt 
 echo  "Files foo.txt and bat.txt created with random content."
```
Откройте файл.
```python
f = open('foo.txt', 'rt')     # Open for reading (text)
g = open('bar.txt', 'wt')     # Open for writing (text)
```

Прочтите все данные.

```python
data = f.read()

# Read only up to 'maxbytes' bytes
data = f.read([maxbytes])
```

Напишите какой-нибудь текст.

```python
g.write('some text')
```

Закройте, когда закончите.

```python
f.close()
g.close()
```

Файлы должны быть правильно закрыты, и об этом легко забыть. Таким образом, предпочтительным подходом является использование такого оператора `with`.

```python
with open(filename, 'rt') as file:
    # Use the file `file`
    ...
    # No need to close explicitly
...statements
```

Это автоматически закрывает файл, когда элемент управления покидает блок кода с отступом.

#### Распространенные идиомы чтения данных файла

Прочитайте весь файл сразу как строку.

```python
with open('foo.txt', 'rt') as file:
    data = file.read()
    # `data` is a string with all the text in `foo.txt`
```

Прочитайте файл построчно, итерируя.

```python
with open(filename, 'rt') as file:
    for line in file:
        # Process the line
```

#### Распространенные идиомы записи в файл

Запись строковых данных.

```python
with open('outfile', 'wt') as out:
    out.write('Hello World\n')
    ...
```

Перенаправьте функцию печати.

```python
with open('outfile', 'wt') as out:
    print('Hello World', file=out)
    ...
```

### Функции

Когда ваши программы начнут становиться больше, вам захочется их организовать. Эта секция кратко представляет функции и библиотечные модули. Также представлена обработка ошибок с исключениями.

#### Пользовательские функции

Используйте функции для кода, который вы хотите использовать повторно. Вот определение функции:

```python
def sumcount(n):
    '''
    Returns the sum of the first n integers
    '''
    total = 0
    while n > 0:
        total += n
        n -= 1
    return total
```

Чтобы вызвать функцию.

```python
a = sumcount(100)
```

Функция — это серия операторов, которые выполняют некоторую задачу и возвращают результат. Ключевое слово `return` необходимо для явного указания возвращаемого значения функции.

#### Библиотечные функции

Python поставляется с большой стандартной библиотекой. Доступ к библиотечным модулям осуществляется с помощью импорта. Например:

```python
import math
x = math.sqrt(10)

import urllib.request
u = urllib.request.urlopen('http://www.python.org/')
data = u.read()
```
#### Ошибки и исключения

Функции сообщают об ошибках как об исключениях. Исключение приводит к прерыванию функции и может привести к остановке всей вашей программы, если ее не обработать.

Попробуйте это в своем REPL на Python.

```python
>>> int('N/A')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'N/A'
>>>
```

В целях отладки сообщение описывает, что произошло, где произошла ошибка, и обратная трассировка, показывающая вызовы других функций, которые привели к сбою.

#### Перехват и обработка исключений


Исключения можно перехватывать и обрабатывать.

Чтобы перехватить, используйте оператор `try - except`.

```python
for line in file:
    fields = line.split(',')
    try:
        shares = int(fields[1])
    except ValueError:
        print("Couldn't parse", line)
    ...
```

Имя `ValueError` должно соответствовать типу ошибки, которую вы пытаетесь отловить.

Часто бывает трудно точно определить, какие ошибки могут возникнуть, заранее в зависимости от выполняемой операции. К лучшему или хуже того, обработка исключений часто добавляется *после* того, как программа
неожиданно произошел сбой (т. е. «Ой, мы забыли отловить эту ошибку. Мы должен справиться с этим!»).

#### Вызов исключений

Чтобы вызвать исключение, используйте оператор `raise`.

```python
raise RuntimeError('What a kerfuffle')
```

Это приведет к аварийному завершению программы с отслеживанием исключений. Если только не пойман блоком `try-except`.

```bash
% python3 foo.py
Traceback (most recent call last):
  File "foo.py", line 21, in <module>
    raise RuntimeError("What a kerfuffle")
RuntimeError: What a kerfuffle
```



### Контейнеры

В этом разделе обсуждаются списки, словари и множества.

#### Обзор

Программам часто приходится работать со многими объектами.

* Портфель акций
* Таблица цен на акции

Есть три основных варианта использования.

* Списки. Заказанные данные.
* Словари. Неупорядоченные данные.
* Наборы. Неупорядоченная коллекция уникальных предметов.

#### Списки как контейнер

Используйте список, когда порядок данных имеет значение. Помните, что списки могут содержать объекты любого типа.
Например, список кортежей.

```python
portfolio = [
    ('GOOG', 100, 490.1),
    ('IBM', 50, 91.3),
    ('CAT', 150, 83.44)
]

portfolio[0]            # ('GOOG', 100, 490.1)
portfolio[2]            # ('CAT', 150, 83.44)
```

#### Построение списка

Создание списка с нуля.

```python
records = []  # Initial empty list

# Use .append() to add more items
records.append(('GOOG', 100, 490.10))
records.append(('IBM', 50, 91.3))
...
```

Пример при чтении записей из файла.

```python
records = []  # Initial empty list

with open('Data/portfolio.csv', 'rt') as f:
    next(f) # Skip header
    for line in f:
        row = line.split(',')
        records.append((row[0], int(row[1]), float(row[2])))
```

#### Словари как контейнер

Словари полезны, если вам нужен быстрый случайный поиск (по имени ключа). Пример, словарь цен на акции:

```python
prices = {
   'GOOG': 513.25,
   'CAT': 87.22,
   'IBM': 93.37,
   'MSFT': 44.12
}
```

Вот несколько простых поисков:

```python
>>> prices['IBM']
93.37
>>> prices['GOOG']
513.25
>>>
```

#### Создание словарей

Пример построения словаря с нуля.

```python
prices = {} # Initial empty dict

# Insert new items
prices['GOOG'] = 513.25
prices['CAT'] = 87.22
prices['IBM'] = 93.37
```

Пример заполнения dict из содержимого файла.

```python
prices = {} # Initial empty dict

with open('Data/prices.csv', 'rt') as f:
    for line in f:
        row = line.split(',')
        prices[row[0]] = float(row[1])
```

#### Поиск по словарю

Вы можете проверить существование ключа.

```python
if key in d:
    # YES
else:
    # NO
```

Вы можете найти значение, которое может не существовать, и указать значение по умолчанию, если оно не существует.

```python
name = d.get(key, default)
```

Пример:

```python
>>> prices.get('IBM', 0.0)
93.37
>>> prices.get('SCOX', 0.0)
0.0
>>>
```

#### Составные ключи

Практически любой тип значения может использоваться в качестве ключа словаря в `Python`. Ключ словаря должен иметь неизменяемый тип.
Например, кортежи:

```python
holidays = {
  (1, 1) : 'New Years',
  (3, 14) : 'Pi day',
  (9, 13) : "Programmer's day",
}
```

Затем для доступа:

```python
>>> holidays[3, 14]
'Pi day'
>>>
```

*Ни список, ни набор, ни другой словарь не могут служить ключом словаря, поскольку списки и словари изменяемы.*

#### Наборы

Наборы — это наборы неупорядоченных уникальных предметов.

```python
tech_stocks = { 'IBM','AAPL','MSFT' }
# Alternative syntax
tech_stocks = set(['IBM', 'AAPL', 'MSFT'])
```

Наборы полезны для тестов членства.

```python
>>> tech_stocks
set(['AAPL', 'IBM', 'MSFT'])
>>> 'IBM' in tech_stocks
True
>>> 'FB' in tech_stocks
False
>>>
```

Наборы также полезны для устранения дубликатов.

```python
names = ['IBM', 'AAPL', 'GOOG', 'IBM', 'GOOG', 'YHOO']

unique = set(names)
# unique = set(['IBM', 'AAPL','GOOG','YHOO'])
```

Дополнительные операции над множеством:

```python
unique.add('CAT')        # Add an item
unique.remove('YHOO')    # Remove an item

s1 = { 'a', 'b', 'c'}
s2 = { 'c', 'd' }
s1 | s2                 # Set union { 'a', 'b', 'c', 'd' }
s1 & s2                 # Set intersection { 'c' }
s1 - s2                 # Set difference { 'a', 'b' }
```




### Форматирование

Этот раздел представляет собой небольшое отступление, но когда вы работаете с данными, вы часто требуется создавать структурированный вывод (таблицы и т. д.). Например:

```code
      Name      Shares        Price
----------  ----------  -----------
        AA         100        32.20
       IBM          50        91.10
       CAT         150        83.44
      MSFT         200        51.23
        GE          95        40.37
      MSFT          50        65.10
       IBM         100        70.44
```

#### Форматирование строк

Один из способов форматирования строки в Python 3.6+ — использование `f-strings`.

```python
>>> name = 'IBM'
>>> shares = 100
>>> price = 91.1
>>> f'{name:>10s} {shares:>10d} {price:>10.2f}'
'       IBM        100      91.10'
>>>
```


Часть `{выражение:формат}` заменяется.

Обычно он используется с `print`.

```python
print(f'{name:>10s} {shares:>10d} {price:>10.2f}')
```

#### Коды форматирования

Коды форматирования (после `:` внутри `{}`) аналогичны `printf()` в C:

```code
d       Decimal integer
b       Binary integer
x       Hexadecimal integer
f       Float as [-]m.dddddd
e       Float as [-]m.dddddde+-xx
g       Float, but selective use of E notation
s       String
c       Character (from integer)
```

Общие модификаторы регулируют ширину поля и десятичную точность. Это неполный список:
```code
:>10d   Integer right aligned in 10-character field
:<10d   Integer left aligned in 10-character field
:^10d   Integer centered in 10-character field
:0.2f   Float with 2 digit precision
```

#### Форматирование словаря

Вы можете использовать метод `format_map()` для применения форматирования строк к словарю значений:

```python
>>> s = {
    'name': 'IBM',
    'shares': 100,
    'price': 91.1
}
>>> '{name:>10s} {shares:10d} {price:10.2f}'.format_map(s)
'       IBM        100      91.10'
>>>
```

Он использует те же коды, что и `f-строки`, но берет значения из прилагаемый словарь.

#### Метод `format()`

Существует метод `format()`, который может применять форматирование к аргументам или ключевые аргументы.

```python
>>> '{name:>10s} {shares:10d} {price:10.2f}'.format(name='IBM', shares=100, price=91.1)
'       IBM        100      91.10'
>>> '{:>10s} {:10d} {:10.2f}'.format('IBM', 100, 91.1)
'       IBM        100      91.10'
>>>
```

Честно говоря, `format()` немного многословен.

#### Форматирование в стиле C

Вы также можете использовать оператор форматирования `%`.

```python
>>> 'The value is %d' % 3
'The value is 3'
>>> '%5d %-5d %10d' % (3,4,5)
'    3 4              5'
>>> '%0.2f' % (3.1415926,)
'3.14'
```

Для этого требуется один элемент или кортеж справа. Коды формата также смоделирован по образцу C `printf()`.

> *Примечание. Это единственное форматирование, доступное для байтовых строк.*

```python
>>> b'%s has %d messages' % (b'Dave', 37)
b'Dave has 37 messages'
>>> b'%b has %d messages' % (b'Dave', 37)  # %b may be used instead of %s
b'Dave has 37 messages'
>>>
```



###  Последовательности

#### Типы данных последовательности


Python имеет три типа данных *последовательность*.

* Строка: `'Привет'`. Строка представляет собой последовательность символов.
* Список: `[1, 4, 5]`.
* Кортеж: `('GOOG', 100, 490.1)`.

Все последовательности упорядочены, индексированы целыми числами и имеют длину.

```python
a = 'Hello'               # String
b = [1, 4, 5]             # List
c = ('GOOG', 100, 490.1)  # Tuple

# Indexed order
a[0]                      # 'H'
b[-1]                     # 5
c[1]                      # 100

# Length of sequence
len(a)                    # 5
len(b)                    # 3
len(c)                    # 3
```

Последовательности могут быть реплицированы: `s * n`.

```python
>>> a = 'Hello'
>>> a * 3
'HelloHelloHello'
>>> b = [1, 2, 3]
>>> b * 2
[1, 2, 3, 1, 2, 3]
>>>
```

Последовательности одного типа могут быть объединены: `s + t`.

```python
>>> a = (1, 2, 3)
>>> b = (4, 5)
>>> a + b
(1, 2, 3, 4, 5)
>>>
>>> c = [1, 5]
>>> a + c
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: can only concatenate tuple (not "list") to tuple
```

#### Нарезка

Нарезка означает выделение подпоследовательности из последовательности. Синтаксис: `s[start:end]`. Где «начало» и «конец» — это индексы нужной подпоследовательности.

```python
a = [0,1,2,3,4,5,6,7,8]

a[2:5]    # [2,3,4]
a[-5:]    # [4,5,6,7,8]
a[:3]     # [0,1,2]
```

* Индексы `start` и `end` должны быть целыми числами.
* Срезы *не* включают конечное значение. Это как полуоткрытый интервал из математики.
* Если индексы опущены, по умолчанию они указывают на начало или конец списка.

#### Переназначение фрагмента

В списках фрагменты можно переназначать и удалять.

```python
# Reassignment
a = [0,1,2,3,4,5,6,7,8]
a[2:4] = [10,11,12]       # [0,1,10,11,12,4,5,6,7,8]
```

> *Примечание. Переназначенный фрагмент не обязательно должен иметь одинаковую длину.*

```python
# Deletion
a = [0,1,2,3,4,5,6,7,8]
del a[2:4]                # [0,1,4,5,6,7,8]
```

#### Сокращение последовательности

Существует несколько общих функций, позволяющих свести последовательность к одному значению.

```python
>>> s = [1, 2, 3, 4]
>>> sum(s)
10
>>> min(s)
1
>>> max(s)
4
>>> t = ['Hello', 'World']
>>> max(t)
'World'
>>>
```

#### Итерация по последовательности

Цикл `for` перебирает элементы последовательности.

```python
>>> s = [1, 4, 9, 16]
>>> for i in s:
...     print(i)
...
1
4
9
16
>>>
```

На каждой итерации цикла вы получаете новый элемент для работы. Это новое значение помещается в переменную итерации. В этом примере переменная итерации равна `x`:

```python
for x in s:         # `x` is an iteration variable
    ...statements
```

На каждой итерации предыдущее значение переменной итерации перезаписывается (если есть). После завершения цикла переменная сохраняет последнее значение.

#### Оператор разрыва

Вы можете использовать оператор `break` для досрочного выхода из цикла.

```python
for name in namelist:
    if name == 'Jake':
        break
    ...
    ...
statements
```

Когда выполняется оператор `break`, он выходит из цикла и перемещается по следующим `statements`. Оператор `break` применяется только к самый внутренний цикл. Если этот цикл находится внутри другого цикла, он не будет
разорвать внешний цикл.

#### Оператор продолжения

Чтобы пропустить один элемент и перейти к следующему, используйте оператор continue.

```python
for line in lines:
    if line == '\n':    # Skip blank lines
        continue
    # More statements
    ...
```

Это полезно, когда текущий элемент не представляет интереса или его нужно игнорировать при обработке.

#### Цикл по целым числам

Если вам нужно посчитать, используйте range().

```python
for i in range(100):
    # i = 0,1,...,99
```

Синтаксис: `range(start, end, step)`

```python
for i in range(100):
    # i = 0,1,...,99
for j in range(10,20):
    # j = 10,11,..., 19
for k in range(10,50,2):
    # k = 10,12,...,48
    # Notice how it counts in steps of 2, not 1.
```

* Конечное значение никогда не включается. Он отражает поведение срезов.
* `start` не является обязательным. По умолчанию `0`.
* `step` не является обязательным. По умолчанию `1`.
* `range()` вычисляет значения по мере необходимости. На самом деле он не хранит большой диапазон чисел.

#### функция перечисления

Функция `enumerate` добавляет к итерации дополнительное значение счетчика.

```python
names = ['Elwood', 'Jake', 'Curtis']
for i, name in enumerate(names):
    # Loops with i = 0, name = 'Elwood'
    # i = 1, name = 'Jake'
    # i = 2, name = 'Curtis'
```

Общая форма — `enumerate(sequence [, start = 0])`. `start` не является обязательным. Хорошим примером использования enumerate() является отслеживание номеров строк при чтении файла:

```python
with open(filename) as f:
    for lineno, line in enumerate(f, start=1):
        ...
```

В конце концов, `enumerate` — это просто хороший ярлык для:

```python
i = 0
for x in s:
    statements
    i += 1
```

Использование `enumerate` требует меньше ввода и работает немного быстрее.

#### Циклы и кортежей

Вы можете выполнять итерацию с несколькими переменными итерации.

```python
points = [
  (1, 4),(10, 40),(23, 14),(5, 6),(7, 8)
]
for x, y in points:
    # Loops with x = 1, y = 4
    #            x = 10, y = 40
    #            x = 23, y = 14
    #            ...
```

При использовании нескольких переменных каждый кортеж *распаковывается* в набор переменных итерации.
Количество переменных должно соответствовать количеству элементов в каждом кортеже.

#### функция zip()

Функция `zip` принимает несколько последовательностей и создает итератор, который их объединяет.

```python
columns = ['name', 'shares', 'price']
values = ['GOOG', 100, 490.1 ]
pairs = zip(columns, values)
# ('name','GOOG'), ('shares',100), ('price',490.1)
```

Чтобы получить результат, необходимо выполнить итерацию. Вы можете использовать несколько переменных для распаковки кортежей, как показано ранее.

```python
for column, value in pairs:
    ...
```

Обычно `zip` используется для создания пар `ключ/значение` для построения словарей.

```python
d = dict(zip(columns, values))
```

### Взаимодействие со списками

Распространенной задачей является обработка элементов в списке. В этом разделе представлены понятия списков,
мощный инструмент для этого.

#### Создание новых списков

Понимание списка создает новый список, применяя операцию к каждый элемент последовательности.

```python
>>> a = [1, 2, 3, 4, 5]
>>> b = [2*x for x in a ]
>>> b
[2, 4, 6, 8, 10]
>>>
```

Другой пример:

```python
>>> names = ['Elwood', 'Jake']
>>> a = [name.lower() for name in names]
>>> a
['elwood', 'jake']
>>>
```
Общий синтаксис: `[ <expression> for <variable_name> in <sequence> ]`.

#### Фильтрация

Вы также можете фильтровать во время понимания списка.

```python
>>> a = [1, -5, 4, 2, -2, 10]
>>> b = [2*x for x in a if x > 0 ]
>>> b
[2, 8, 4, 20]
>>>
```

#### Случаи использования

Понимание списков чрезвычайно полезно. Например, вы можете собирать значения определенного поля словаря:

```python
stocknames = [s['name'] for s in stocks]
```

Вы можете выполнять запросы к последовательностям, аналогичные базе данных.

```python
a = [s for s in stocks if s['price'] > 100 and s['shares'] > 50 ]
```

Вы также можете объединить понимание списка с сокращением последовательности:

```python
cost = sum([s['shares']*s['price'] for s in stocks])
```

#### Общий синтаксис

```code
[ <expression> for <variable_name> in <sequence> if <condition>]
```

Что это значит:

```python
result = []
for variable_name in sequence:
    if condition:
        result.append(expression)
```

#### Исторический экскурс

Понимание списков происходит из математики (нотация построителя множеств).

```code
a = [ x * x for x in s if x > 0 ] # Python

a = { x^2 | x ∈ s, x > 0 }         # Math
```

Он также реализован на нескольких других языках. Большинство хотя программисты, вероятно, не думают о своем уроке математики. Так, его можно рассматривать как отличный ярлык для списка.


### Объекты

В этом разделе представлена более подробная информация о внутренней объектной модели Python и обсуждаются некоторые вопросы, связанные с управлением памятью, копированием и проверкой типов.

#### Assignment

Многие операции в Python связаны с *присвоением* или *хранением* значений.

```python
a = value         # Assignment to a variable
s[n] = value      # Assignment to a list
s.append(value)   # Appending to a list
d['key'] = value  # Adding to a dictionary
```

*Предупреждение: операции присваивания **никогда не создают копию** присваиваемого значения.*
Все назначения представляют собой просто ссылочные копии (или копии указателей, если хотите).

#### Пример назначения

Рассмотрим этот фрагмент кода.

```python
a = [1,2,3]
b = a
c = [a,b]
```

Изображение основных операций с памятью. В этом примере есть это только один объект списка `[1,2,3]`, но есть четыре разных ссылки на него.

Это означает, что изменение значения влияет на *все* ссылки.

```python
>>> a.append(999)
>>> a
[1,2,3,999]
>>> b
[1,2,3,999]
>>> c
[[1,2,3,999], [1,2,3,999]]
>>>
```

Обратите внимание, как изменения в исходном списке отображаются повсюду. Это потому, что копии никогда не делались. Все указывая на то же самое.

#### Переназначение значений

Переназначение значения *никогда* перезаписывает память, занятую предыдущим значением.

```python
a = [1,2,3]
b = a
a = [4,5,6]

print(a)      # [4, 5, 6]
print(b)      # [1, 2, 3]    Holds the original value
```

Помните: **Переменные — это имена, а не ячейки памяти.**


#### Идентификация и ссылки

Используйте оператор `is`, чтобы проверить, являются ли два значения одним и тем же объектом.

```python
>>> a = [1,2,3]
>>> b = a
>>> a is b
True
>>>
```

`is` сравнивает идентификатор объекта (целое число). Идентификатор может быть получено с помощью `id()`.

```python
>>> id(a)
3588944
>>> id(b)
3588944
>>>
```

Примечание. Для проверки объектов почти всегда лучше использовать `==`. Поведение `is` часто бывает неожиданным:
```python
>>> a = [1,2,3]
>>> b = a
>>> c = [1,2,3]
>>> a is b
True
>>> a is c
False
>>> a == c
True
>>>
```

#### Мелкие копии
>[справка](https://docs.python.org/3/library/copy.html)

Списки и словари имеют методы копирования.

```python
>>> a = [2,3,[100,101],4]
>>> b = list(a) # Make a copy
>>> a is b
False
```

Это новый список, но элементы списка являются общими.

```python
>>> a[2].append(102)
>>> b[2]
[100,101,102]
>>>
>>> a[2] is b[2]
True
>>>
```

Например, используется общий внутренний список «[100, 101, 102]». Это известно как мелкая копия.


#### Глубокие копии

Иногда вам нужно сделать копию объекта и всех объектов, содержащихся в нем. Для этого вы можете использовать модуль `copy`:

```python
>>> a = [2,3,[100,101],4]
>>> import copy
>>> b = copy.deepcopy(a)
>>> a[2].append(102)
>>> b[2]
[100,101]
>>> a[2] is b[2]
False
>>>
```

#### Имена, значения, типы

Имена переменных не имеют *типа*. Это всего лишь имя. Однако значения *действительно* имеют базовый тип.

```python
>>> a = 42
>>> b = 'Hello World'
>>> type(a)
<type 'int'>
>>> type(b)
<type 'str'>
```

`type()` скажет вам, что это такое. Имя типа обычно используется как функция который создает или преобразует значение в этот тип.


#### Проверка типа

Как определить, относится ли объект к определенному типу.

```python
if isinstance(a, list):
    print('a is a list')
```

Проверка одного из многих возможных типов.

```python
if isinstance(a, (list,tuple)):
    print('a is a list or tuple')
```

*Внимание: не переусердствуйте с проверкой типов. Это может привести к
чрезмерная сложность кода. Обычно вы делаете это только в том случае, если делаете
так вы предотвратите типичные ошибки, допущенные другими людьми при использовании вашего кода.
*

### Все является объектом

Числа, строки, списки, функции, исключения, классы, экземпляры,
и т. д. — все это объекты. Это означает, что все объекты, которым можно дать имя, могут быть
передаваться как данные, помещаться в контейнеры и т. д. без каких-либо
ограничения. Не существует *особых* типов объектов. Иногда это
Говорят, что все объекты `first-class`.

Простой пример:

```python
>>> import math
>>> items = [abs, math, ValueError ]
>>> items
[<built-in function abs>,
  <module 'math' (builtin)>,
  <type 'exceptions.ValueError'>]
>>> items[0](-45)
45
>>> items[1].sqrt(2)
1.4142135623730951
>>> try:
        x = int('not a number')
    except items[2]:
        print('Failed!')
Failed!
>>>
```
Здесь `items` — это список, содержащий функцию, модуль и
исключение. Вы можете напрямую использовать элементы в списке вместо
оригинальные названия:

```python
items[0](-45)       # abs
items[1].sqrt(2)    # math
except items[2]:    # ValueError
```

С большой силой приходит ответственность. То, что вы можете это сделать, не означает, что вы должны это делать.

---
Задания : [[computer science/chapter5/task]]




