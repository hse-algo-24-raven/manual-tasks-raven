# Задача о распределении инвестиций между проектами Green-team

Условия задачи представляются в виде прямоугольной матрицы, где столбцы соответствуют проектам, а строки части инвестиций, направляемых в проекты, объем инвестиций указывается в первом столбце. В ячейках таблицы представлены суммы прибыли от вложения некоторой части средств в определенный проект.

Для решения задачи требуется рассчитать максимально возможную сумму прибыли от вложения всех средств в проекты и распределение этой суммы между проектами.

## Вариант 1

| $   | A   | B   | C   | D   |
|-----|-----|-----|-----|-----|
| 20  | 7   | 2   | 1   | 4   |
| 40  | 9   | 10  | 12  | 13  |
| 60  | 11  | 13  | 14  | 16  |
| 80  | 17  | 15  | 15  | 18  |
| 100 | 21  | 22  | 19  | 19  |

Первым шагом необходимо посчитать максимальную прибыль для A и B.

**Таблица значений для AB**

| $   | A   | B   | AB      |
|-----|-----|-----|---------|
| 20  | 7   | 2   | A1B0 7  |
| 40  | 9   | 10  | A0B2 10 |
| 60  | 11  | 13  | A1B2 17 |
| 80  | 17  | 15  | A1B3 20 |
| 100 | 21  | 22  | A0B5 22 |

Сначала считаем прибыль от 0 до 1 части.

| A   | B   | AB  |
|-----|-----|-----|
| 0   | 1   | 2   |
| 1   | 0   | 7   |

Максимальное значение равно 7, поэтому запишем A1B0 7

Потом считаем прибыль от 0 до 2 части

| A   | B   | AB        |
|-----|-----|-----------|
| 0   | 2   | 10        |
| 1   | 1   | 7 + 2 = 9 |
| 2   | 0   | 9         |

Максимальное значение равно 10, поэтому запишем A0B2 10

Потом считаем прибыль от 0 до 3 части

| A   | B   | AB          |
|-----|-----|-------------|
| 0   | 3   | 13          |
| 1   | 2   | 7 + 10 = 17 |
| 2   | 1   | 9 + 2 = 11  |
| 3   | 0   | 11          |

Максимальное значение равно 17, поэтому запишем A1B2 17

Потом считаем прибыль от 0 до 4 части

| A   | B   | AB          |
|-----|-----|-------------|
| 0   | 4   | 15          |
| 1   | 3   | 7 + 13 = 20 |
| 2   | 2   | 9 + 10 = 19 |
| 3   | 1   | 11 + 2 = 13 |
| 4   | 0   | 17          |

Максимальное значение равно 20, поэтому запишем A1B3 20

Потом считаем прибыль от 0 до 5 части

| A   | B   | AB           |
|-----|-----|--------------|
| 0   | 5   | 22           |
| 1   | 4   | 7 + 15 = 22  |
| 2   | 3   | 9 + 13 = 22  |
| 3   | 2   | 11 + 10 = 21 |
| 4   | 1   | 17 + 2 = 19  |
| 5   | 0   | 21           |

Максимальное значение равно 22, поэтому можно выбрать либо A0B5, либо A1B4, либо A2B3. Выбирает каждый по вкусу, но мы всегда будем брать первое значение, поэтому выбираем A0B5 и вписываем его в таблицу.

Следующим шагом необходимо посчитать максимальную прибыль для AB и C. Действуем по такой же схеме.

**Таблица значений для ABС**

| $   | A   | B   | AB      | C   | ABC      |
|-----|-----|-----|---------|-----|----------|
| 20  | 7   | 2   | A1B0 7  | 1   | AB1C0 7  |
| 40  | 9   | 10  | A0B2 10 | 12  | AB0C2 12 |
| 60  | 11  | 13  | A1B2 17 | 14  | AB1C2 19 |
| 80  | 17  | 15  | A1B3 20 | 15  | AB2C2 22 |
| 100 | 21  | 22  | A0B5 22 | 19  | AB3C2 29 |

| AB  | C   | ABC |
|-----|-----|-----|
| 0   | 1   | 1   |
| 1   | 0   | 7   |

| AB  | C   | ABC       |
|-----|-----|-----------|
| 0   | 2   | 12        |
| 1   | 1   | 2 + 1 = 3 |
| 2   | 0   | 10        |

| AB  | C   | ABC         |
|-----|-----|-------------|
| 0   | 3   | 14          |
| 1   | 2   | 7 + 12 = 19 |
| 2   | 1   | 10 + 1 = 11 |
| 3   | 0   | 17          |

| AB  | C   | ABC          |
|-----|-----|--------------|
| 0   | 4   | 15           |
| 1   | 3   | 7 + 14 = 21  |
| 2   | 2   | 10 + 12 = 22 |
| 3   | 1   | 17 + 1 = 18  |
| 4   | 0   | 20           |

| AB  | C   | ABC          |
|-----|-----|--------------|
| 0   | 5   | 19           |
| 1   | 4   | 7 + 15 = 22  |
| 2   | 3   | 10 + 14 = 24 |
| 3   | 2   | 17 + 12 = 29 |
| 4   | 1   | 20 + 1 = 21  |
| 5   | 0   | 22           |

Осталось посчитать только значение для D, поэтому считаем только прибыль от 0 до 5 части для ABC и D.

**Таблица значений для ABСD**

| $   | A   | B   | AB      | C   | ABC      | D   | ABCD      |
|-----|-----|-----|---------|-----|----------|-----|-----------|
| 20  | 7   | 2   | A1B0 7  | 1   | AB1C0 7  | 4   |           |
| 40  | 9   | 10  | A0B2 10 | 12  | AB0C2 12 | 13  |           |
| 60  | 11  | 13  | A1B2 17 | 14  | AB1C2 19 | 16  |           |
| 80  | 17  | 15  | A1B3 20 | 15  | AB2C2 22 | 18  |           |
| 100 | 21  | 22  | A0B5 22 | 19  | AB3C2 29 | 19  | ABC3D2 32 |

| ABC | D   | ABCD         |
|-----|-----|--------------|
| 0   | 5   | 19           |
| 1   | 4   | 7 + 18 = 25  |
| 2   | 3   | 12 + 16 = 28 |
| 3   | 2   | 19 + 13 = 32 |
| 4   | 1   | 22 + 4 = 26  |
| 5   | 0   | 29           |

Максимальное значение равно 32, значит вписываем в пятую ячейку ABC3D2 32. Это будет максимальная возможная прибыль.

**Проверка**

D2 = 13; C2 = 12; B0 = 0; A1 = 7 => 13 + 12 + 7 = 32 - Верно

D2 = 40$; C2 = 40$; A1 = 20$ => 40 + 40 + 20 = 100$ - Верно



