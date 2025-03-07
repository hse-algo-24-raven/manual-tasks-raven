# Задача о рюкзаке (Knapsack problem). Генетический алгоритм

## Задание
Для каждого варианта представлены условия задачи, в соответствии с которыми необходимо: 
1. Решить задачу о рюкзаке с применением генетического алгоритма.
2. Оформить решение задачи по шагам с подробными комментариями, таблицами и диаграммами.
3. В ответе указать:
   - максимально возможную стоимость предметов в рюкзаке,
   - набор предметов, обеспечивающих максимальную стоимость,
   - общий вес предметов в рюкзаке,
   - свободное место в рюкзаке.

## Вариант 10
Решить задачу о рюкзаке с применением генетического алгоритма, с учетом следующих требований:
   - Придумать условия задачи с количеством предметов не менее 7.
   - Численность популяции не менее 8 особей, в скрещивании участвует половина популяции. 
   - Для скрещивания выбираются сильнейшие особи, скрещивание – равномерное.
   - До выполнения алгоритма сформулировать стратегию применения оператора мутации.
   - Сформировать не менее 3 поколений, не считая первоначального.


## Задача

Даны предметы в рюкзаке, их масса и стоимость

| Предметы  | A  | B  | C  | D  | E  | F  | G  |
|:----------|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Стоимость | 3  | 8  | 6  | 10 | 7  | 5  | 4  |
| Вес       | 2  | 5  | 4  | 6  | 4  | 3  | 2  |

Максимальный вес рюкзака - 15

**Мутация:**
Оператор мутации применяется в одном случайном гене, если два поколения подряд не произошло улучшения лидирующего решения, либо если потомок оказался недееспособным (это значит что его вес превышает допустимый). Если потомок остается недееспособным после первой мутации, он исключается из популяции. Также мутация применяется, если потомок полностью повторяет одну из существующих особей, чтобы избежать дублирования решений. Если после мутации вес особи превышает допустимый, удаляются наименее ценные предметы до достижения допустимого веса.

## Решение

### 1 поколение

**Формирование популяции**

Сформируем особи, будем обозначать особи строками из 0 и 1, где 0 - предмет не взяли, 1 - взяли

Создадим 8 строк (особей) случаным образом из 0 и 1.

1) 0010101
2) 0010001
3) 1110111
4) 1011101
5) 1001100
6) 0110010
7) 0001011
8) 1010110

Теперь посчитаем фитнес-функции для каждого

1) f(x1) = 17
2) f(x2) = 10
3) f(x3) = 0 -> не жизнеспособен (вес 20) надо мутировать -> 0110101 тогда теперь фитнес-функция равна 25
4) f(x4) = 0 -> не жизнеспособен (вес 18) надо мутировать -> 1010101 тогда теперь фитнес-функция равна 20
5) f(x5) = 20
6) f(x6) = 19
7) f(x7) = 19
8) f(x8) = 21

### Отбор
Для скрещивания возьмем x3, x4, x8, x5 (самые жизнеспособные особи)

### Новое поколение

Будем скрещивать особи так: x3-x8, x4-x5

Так как скрещивание равномерное, то введем вспомогательную строчку y из 0 и 1. Тем самым она дает правило для скрещивания: будет относиться ген к первому потомку или ко второму. Если 0, то ген первого родителя передается 1 потомку, а второго родителя 2, если 1, то 1 потомку идет ген второго родителя, а 2 - первого.

Скрещиваем x3-x8:
y =  1010110
x3=  0110101
x8=  1010110
x9=  1110111
x10= 0010100

f(x9) = 0 (превышает вес)
проведём случайную мутацию для 2 гена
тогда x9 = 1010111
и f(x9) = 25

f(x10) = 13

Скрещиваем x4-x5:

y =  0110110
x4=  1010101
x5=  1001100
x11= 1000101
x12= 1011100

f(x11) = 14
f(x12) = 0 (превышает вес)
 
проведём случайную мутацию для x12

x12 = 1001101

f(x12) = 24

### Поколение 2
В новое поколения войду только самые приспособленные особи.

- x1:  (0010101) f(x)= 17
- x2:  (0010001) f(x)= 10
- x3:  (0110101) f(x)= 25
- x4:  (1010101) f(x)= 20
- x5:  (1001100) f(x)= 20
- x6:  (0110010) f(x)= 19
- x7:  (0001011) f(x)= 19
- x8:  (1010110) f(x)= 21
- x9:  (1010111) f(x)= 25
- x10: (0010100) f(x)= 13
- x11: (1000101) f(x)= 14
- x12: (1001101) f(x)= 24

8 самых приспособленных:

- x3:  (0110101) f(x)= 25
- x4:  (1010101) f(x)= 20
- x5:  (1001100) f(x)= 20
- x6:  (0110010) f(x)= 19
- x7:  (0001011) f(x)= 19
- x8:  (1010110) f(x)= 21
- x9:  (1010111) f(x)= 25
- x12: (1001101) f(x)= 24

### Отбор
Для скрещивания возьмем x3, x8, x9, x12 (самые жизнеспособные особи)

### Новое поколение

Будем скрещивать особи так: x3-x9, x8-x12

Так как скрещивание равномерное, то введем вспомогательную строчку y из 0 и 1. Тем самым она дает правило для скрещивания: будет относиться ген к первому потомку или ко второму. Если 0, то ген первого родителя передается 1 потомку, а второго родителя 2, если 1, то 1 потомку идет ген второго родителя, а 2 - первого.

Скрещиваем x3-x9:
y =  1010011
x3=  0110101
x9=  1010111
x13= 1110111
x14= 0010101

f(x13) = 0 (превышает вес)

Проведем случайную мутацию:
x13 = 0100111
f(x13) = 24

f(x14) = 17 

Скрещиваем x8-x12:

y =  1011100
x8=  1010110
x12= 1001101
x15= 1001110 
x16= 1010101

f(x15) = 25
f(x16) = 20 (повторяет особь x4)
проведем случайную мутацию для x16

x16 = 1010100
f(x16) = 16

### Поколение 3
**Отбор**
- x3:  (0110101) f(x) = 25
- x4:  (1010101) f(x) = 20
- x5:  (1001100) f(x) = 20
- x6:  (0110010) f(x) = 19
- x7:  (0001011) f(x) = 19
- x8:  (1010110) f(x) = 21
- x9:  (1010111) f(x) = 25
- x12: (1001101) f(x) = 24
- x13: (0100111) f(x) = 24
- x14: (0010101) f(x) = 17
- x15: (1001110) f(x) = 25
- x16: (1010100) f(x) = 16


8 самых приспособленных:
- x3:  (0110101) f(x) = 25
- x4:  (1010101) f(x) = 20
- x5:  (1001100) f(x) = 20
- x8:  (1010110) f(x) = 21
- x9:  (1010111) f(x) = 25
- x12: (1001101) f(x) = 24
- x13: (0100111) f(x) = 24
- x15: (1001110) f(x) = 25

### Отбор
Для скрещивания возьмем x3, x9, x12, x15 (самые жизнеспособные особи)

### Новое поколение

Будем скрещивать особи так: x3-x12, x9-x15

Так как скрещивание равномерное, то введем вспомогательную строчку y из 0 и 1. Тем самым она дает правило для скрещивания: будет относиться ген к первому потомку или ко второму. Если 0, то ген первого родителя передается 1 потомку, а второго родителя 2, если 1, то 1 потомку идет ген второго родителя, а 2 - первого.

Скрещиваем x3-x12:
y =  0010011
x3=  0110101
x12= 1001101
x17= 0100101
x18= 1011101

f(x17) = 19

f(x18) = 0 (превышает вес)

Проведём мутацию для x18:
x18 = 1011001

f(x18) = 23

Скрещиваем x9-x15:
y =  0111011
x9=  1010111
x15= 1001110
x19= 1001110
x20= 1010111

так как x19 получился такой же как и его потомок (x15), проведем мутацию x19

x19 = 1101101
f(x19) = 0 (превышает вес)

Повторим мутацию:
x19 = 1101100
f(x19) = 0 (превышает вес) - мутации больше не проводятся, особь не жизнеспособна

так как x20 получился такой же как и его потомок (x19), проведем мутацию x20

x20 = 1110110

f(x20) =  0 (превышает вес)

Повторим мутацию:

x20 = 1110100
f(x20) = 24

### 4 поколение
**Отбор**

- x3:  (0110101) f(x) = 25
- x4:  (1010101) f(x) = 20
- x5:  (1001100) f(x) = 20
- x8:  (1010110) f(x) = 21
- x9:  (1010111) f(x) = 25
- x12: (1001101) f(x) = 24
- x13: (0100111) f(x) = 24
- x15: (1001110) f(x) = 25
- x17: (0100101) f(x) = 19
- x18: (1011001) f(X) = 23
- x20: (1110100) f(x) = 24

8 самых приспособленных:
- x3:  (0110101) f(x) = 25
- x8:  (1010110) f(x) = 21
- x9:  (1010111) f(x) = 25
- x12: (1001101) f(x) = 24
- x13: (0100111) f(x) = 24
- x15: (1001110) f(x) = 25
- x18: (1011001) f(X) = 23
- x20: (1110100) f(x) = 24

Приостановим решение задачи и получим ответ на текущем моменте решения

Выберем лучшее решение: x3, x9, x15

Имеется несколько максимальных стоимосте равных 25

### Ответ

Максимальная возможная стоимость предметов: 25

Набор таких предметов, которые дают стоимость 25:
1: B, C, E, G
2: A, C, E, F, G
3: A, D, E, F

