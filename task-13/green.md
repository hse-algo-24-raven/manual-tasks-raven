# Задача о рюкзаке (Knapsack problem). Генетический алгоритм. Green
### Вариант 3:
Решить задачу о рюкзаке с применением генетического алгоритма, с учетом следующих требований:
   - Придумать условия задачи с количеством предметов не менее 9.
   - Численность популяции не менее 4 особей, в скрещивании участвует половина популяции. 
   - Для скрещивания выбираются победители турнира, скрещивание – одноточечное.
   - До выполнения алгоритма сформулировать стратегию применения оператора мутации.
   - Сформировать не менее 3 поколений, не считая первоначального.

## Условия задачи:

| Предметы  |  A  |  B  |  C  |  D  |  E  |  F  |  G  |  H  |  I  |
|:----------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Стоимость |  5  |  3  |  8  | 18  |  8  |  14 |  21 |  12 |  16 |
| Вес       | 11  | 9   |  4  |  6  |  2  |  10 |  12 |  6  |  3  |

Ограничение вместимости: 35

Численность популяции составляет 4 особи, в скрещивание участвуют 2 особи. 
Для скрещивания выбираются победители турнира, скрещивание – одноточечное.
Мутация реализована как инверсия случайного бита и применяется, 
если вместимость потомка превышает ограничение вместимости (в такой ситуации случаный 1 заменим на 0) 
или подобная особь уже есть в популяции, а также если особь была победителем в двух прошлых поколения.


## Решение:

### Первое поколение
   - X1 110110001 - вес: 31, стоимость: 50
   - X2 011010110 - вес: 33, стоимость: 52
   - X3 011001100 - вес: 35, стоимость: 46
   - X4 100110011 - вес: 28, стоимость: 59

### Отбор:
Сравниваем: X1 < X2; X3 < X4.
Выбираем победителей: 100110011 (59) и 011010110 (52)

### Скрещивание:
- X4: 10011 | 0011
- X2: 01101 | 0110

Потомки:
- X5 100110110 (вес 37, превышение) -> мутация -> 100010110 (вес 31 (11 + 2 + 12 + 6), стоимость 46 (5 + 8 + 21 + 12))
- X6 011010011 (вес 24 (9 + 4 + 2 + 6 + 3), стоимость 30 (3 + 8 + 8 + 12 + 16))

### Второе поколение:
- X1 110110001 - вес: 31, стоимость: 50
- X2 011010110 - вес: 33, стоимость: 52
- X3 011001100 - вес: 35, стоимость: 46
- X4 100110011 - вес: 28, стоимость: 59
- X5 100010110 - вес: 31, стоимость: 46
- X6 011010011 - вес: 30, стоимость: 30

### Оставляем лучших:
- X1 110110001 - вес: 31, стоимость: 50
- X2 011010110 - вес: 33, стоимость: 52
- X4 100110011 - вес: 28, стоимость: 59
- X5 100010110 - вес: 31, стоимость: 46

### Второй отбор:
Сравниваем: X4 > X2; X1 > X5.
Выбираем победителей: 100110011 (59) и 110110001 (50)

### Cкрещивание:
- X4: 100 | 110011
- X1: 110 | 110001

| Предметы  |  A  |  B  |  C  |  D  |  E  |  F  |  G  |  H  |  I  |
|:----------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Стоимость |  5  |  3  |  8  | 18  |  8  |  14 |  21 |  12 |  16 |
| Вес       | 11  | 9   |  4  |  6  |  2  |  10 |  12 |  6  |  3  |

Потомки:
- X7 100110001 (вес 22 (11 + 6 + 2 + 3), стоимость 47 (5 + 18 + 8 + 16))
- X8 110110011 (вес 37 (11 + 9 + 6 + 2 + 6 + 3), превышение -> мутация -> 010110011 26(9 + 6 + 2 + 6 + 3), стоимость 57 (3 + 18 + 8 + 12 + 16))

### Третье поколение:
- X1 110110001 - вес: 31, стоимость: 50
- X2 011010110 - вес: 33, стоимость: 52
- X4 100110011 - вес: 28, стоимость: 59, победила два раза -> мутация -> X4 100100011 - вес: 26 (11 + 6 + 6 + 3), стоимость: 51 (5 + 18 + 12 + 16)
- X5 100010110 - вес: 31, стоимость: 46
- X7 100110001 - вес: 22, стоимость: 47
- X8 010110011 - вес: 26, стоимость: 57
  
### Оставляем лучших:
- X1 110110001 - вес: 31, стоимость: 50
- X2 011010110 - вес: 33, стоимость: 52
- X4 100110011 - вес: 26, стоимость: 51
- X8 010110011 - вес: 26, стоимость: 57

### Отбор:
Сравниваем: X1 < X2; X4 < X8.
Выбираем победителей: 011010110 (52) и 010110011 (57)

### Скрещивание:
- X2: 01101 | 0110
- X8: 01011 | 0011

Потомки:
- X9 011010011 (вес 24(9 + 4 + 2 + 6 + 3), стоимость 47 (3 + 8 + 8 + 12 + 16))
- X10 010110110 (вес 35 (9 + 6 + 2 + 12 + 6), стоимость 62 (3 + 18 + 8 + 21 + 12))

### Четвертое поколение:
- X1 110110001 - вес: 31, стоимость: 50
- X2 011010110 - вес: 33, стоимость: 52, победила два раза -> мутация -> X2 011010111 - вес: 36 (9 + 4 + 2 + 12 + 6 + 3), превышение -> мутация -> X2 001010111, вес: 27 (4 + 2 + 12 + 6 + 3), стоимость 65(8 + 8 + 21 + 12 + 16)
- X4 100110011 - вес: 26, стоимость: 51
- X8 010110011 - вес: 26, стоимость: 57
- X9 011010011 - вес: 24, стоимость: 47
- X10 010110110 - вес: 35, стоимость 62
  
### Оставляем лучших:
- X2 001010111 - вес: 27, стоимость: 65
- X4 100110011 - вес: 26, стоимость: 51
- X8 010110011 - вес: 26, стоимость: 57
- X10 010110110 - вес: 35, стоимость 62

## Остановка выволнение цикла
**Лучшее найденное решение: X10 001010111 (вес 27, стоимость 65)**.

# Ответ:
   - максимально возможную стоимость предметов в рюкзаке - 65;
   - набор предметов, обеспечивающих максимальную стоимость - C, E, G, H, I;
   - общий вес предметов в рюкзаке - 27;
   - свободное место в рюкзаке - 8.