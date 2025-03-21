# Задача о рюкзаке (Knapsack problem). Генетический алгоритм.

### Вариант 5: 
Решить задачу о рюкзаке с применением генетического алгоритма, с учетом следующих требований:
   - Придумать условия задачи с количеством предметов не менее 7.
   - Численность популяции не менее 8 особей, в скрещивании участвует половина популяции. 
   - Для скрещивания выбираются сильнейшие особи, скрещивание – равномерное.
   - До выполнения алгоритма сформулировать стратегию применения оператора мутации.
   - Сформировать не менее 3 поколений, не считая первоначального.

## Условия задачи

Дано 7 предметов, их стоимости и веса:

| Предметы  |  A  | B |  C  | D | E | F | G |
|:----------|:---:|:-:|:---:|:-:|:-:|:-:|:-:|
| Стоимость |  6  | 8 |   6 | 8 | 2 | 3 | 2 |
| Вес       | 16  | 14| 7   | 4 | 15| 5 | 5 |

Максимальный помещающийся в рюкзак вес = 25.

Сформировать 3 поколения (не учитывая первоначальное). Численность популяции 8 особей. В скрещивании участвует половина популяции, то есть 4 особи. Для скрещивания выбираются сильнейшие особи, а само скрещивание - равномерное.

Оператор мутации применяется в одном случайном гене, если два поколения подряд лидер не сменялся, либо если данный потомок оказался недееспособен (второй раз, если он остался недееспособным, мутация не применяется - потомок исключается), либо потомок повторяет одного из особей в популяции.

Если вес особи превышает максимальный допустимый, тогда она считается недееспособной.

## Решение

Будем обозначать строками варианты, где 0 и 1 обозначают взяли ли мы в данном варианте предмет, стоящий в данной позиции, где и данная цифра (0 - не взяли, 1 - взяли).

### Поколение 1
#### Формирование начальной популяции

Возьмём 8 случайных наборов строк (вариантов, особей со случайными генами):

1. (1000001)
2. (0110000)
3. (0000100)
4. (0100001)
5. (0000111)
6. (0101010)
7. (0011011)
8. (0101000)

#### Посчитаем фитнес функции

1. f(x1) = 8
2. f(x2) = 14
3. f(x3) = 2
4. f(x4) = 10
5. f(x5) = 5 
6. f(x6) = 19
7. f(x7) = 19
8. f(x8) = 16

#### Отбор
Для нового поколения возьмём x2, x6, x7, x8 как самых жизнеспособных. Они же однозначно войдут в следующую популяцию.

#### Новое поколение

Скрестим особи таким образом: x2-x6, x7-x8

Скрещивание равномерное, поэтому введём дополнительную переменную t. Она задаёт то, будет ли ген относится к первому потомку или ко второму (от каждой пары по 2 потомка) - 0 значит, что прямое наследование, то есть ген первого родителя передаётся первому потомку, а второго - второму; 1 - наоборот.

Скрещиваем x2-x6: 
- t = (0010101)
- x2= (0110000)
- x6= (0101010)
- x9= (0100000)
- x10=(0111010)

f(x9) = 8

f(x10) = 0 (превышение веса)

Введём случайную мутацию для x10

x10=(0111000)

f(x10) = 22

Скрещиваем x7-x8:
- t = (0100010)
- x7= (0011011)
- x8= (0101000)
- x11=(0111001)
- x12=(0001010)

f(x11) = 0 (превышение веса)

Введём случайную мутацию для x11

x11 = (0110001)

f(x11) = 0 (превышение веса)

f(x12) = 11

### Поколение 2
#### Отбор для нового поколения
- x1:  (1000001) f(x)= 8
- x2:  (0110000) f(x)= 14
- x3:  (0000100) f(x)= 2
- x4:  (0100001) f(x)= 10
- x5:  (0000111) f(x)= 5
- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x9:  (0100000) f(x)= 8
- x10: (0111000) f(x)= 22
- x12: (0001010) f(x)= 11

Отбираем 8 самых приспособленных особей:
- x2:  (0110000) f(x)= 14
- x4:  (0100001) f(x)= 10
- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x9:  (0100000) f(x)= 8
- x10: (0111000) f(x)= 22
- x12: (0001010) f(x)= 11

####  Отбор для скрещивания
Для отбора на скрещивание возьмём 4 самые приспособленные особи: x6, x7, x8, x10

#### Новое поколение
Скрестим их так: x6-x7, x8-x10

x6-x7:
- t =  (0011100)
- x6=  (0101010)
- x7=  (0011011)
- x13= (0111010)
- x14= (0001011)

f(x13) = 0 (превышение веса)

Мутация:

x13 = (0011010)

f(x13) = 17

f(x14) = 13

x8-x10:
- t =  (1101001)
- x8 = (0101000)
- x10= (0111000)
- x15= (0111000)
- x16= (0101000)

Данные особи повторяют две другие особи. Включим мутации для каждой:

- x15= (0011000)
- x16= (0101001)

- f(x15) = 14
- f(x16) = 18

### Поколение 3
#### Отбор для нового поколения

- x2:  (0110000) f(x)= 14
- x4:  (0100001) f(x)= 10
- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x9:  (0100000) f(x)= 8
- x10: (0111000) f(x)= 22
- x12: (0001010) f(x)= 11
- x13: (0011010) f(x)= 17
- x14: (0001011) f(x)= 13
- x15: (0011000) f(x)= 14
- x16: (0101001) f(x)= 18

Отбираем 8 самых приспособленных особей:

- x2:  (0110000) f(x)= 14
- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x10: (0111000) f(x)= 22
- x13: (0011010) f(x)= 17
- x15: (0011000) f(x)= 14
- x16: (0101001) f(x)= 18

#### Отбор для скрещивания
Отберём x6, x7, x10, x16

#### Новое поколение
Скрестим их так: x10-x16, x6-x7
(второе поколение подряд лидер не меняется, поэтому в потомках лидера используем мутацию)

Скрещиваем x10-x16:
- t =  (0011010)
- x10= (0111000)
- x16= (0101001)
- x17= (0101000)
- x18= (0111001)

Применим мутацию:
- x17= (0101100)
- x18= (0011001)

f(x17) = 0 (превышение веса) - не будем повторять мутацию

f(x18) = 16

Скрещиваем x6-x7:
- t =  (1101111)
- x6=  (0101010)
- x7=  (0011011)
- x19= (0001011)
- x20= (0111010)

f(x19) = 13

f(x20) = 0 (превышение веса)

Применим мутацию:

x20 = 1111010

f(x20) = 0 (превышение веса) - второй раз не будем применять мутацию

### Поколение 4
#### Отбор для нового поколения

- x2:  (0110000) f(x)= 14
- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x10: (0111000) f(x)= 22
- x13: (0011010) f(x)= 17
- x15: (0011000) f(x)= 14
- x16: (0101001) f(x)= 18
- x18: (0011001) f(x)= 16
- x19: (0001011) f(x)= 13

Выберем 8 самых приспособленных:

- x6:  (0101010) f(x)= 19
- x7:  (0011011) f(x)= 19
- x8:  (0101000) f(x)= 16
- x10: (0111000) f(x)= 22
- x13: (0011010) f(x)= 17
- x15: (0011000) f(x)= 14
- x16: (0101001) f(x)= 18
- x18: (0011001) f(x)= 16

### Остановка цикла смены поколений
Выбираем лучшее решение из представленных: x10.

## Ответ

Максимально возможная стоимость предметов: 22

Набор предметов, обеспечивающий максимальную стоимость: B, C, D

Общий вес предметов: 25

Свободное место в рюкзаке: 0


