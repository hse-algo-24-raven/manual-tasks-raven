# Вариант 5
Вариант 5:
Имеется 4 независимых задания и 2 исполнителя, исполнитель 1 с производительностью 7 и исполнитель 2 производительностью 3. Длительность заданий составляет 45, 19, 16, 10.


## Запишем, что нам дано
<br>

P<sub>1</sub>  = 7\
P<sub>2</sub> = 3

|A|B|C|D|
|:-|:---:|:----:|---:|
|45|19|16|10|

## Найдем минимальное время, за которое можно сделать все задания
### t<sub>min</sab> = $\frac{A + B + C + D}{P_1 + P_2}$ = $\frac{45 + 19 + 16 + 10}{7 + 3}$ = 9
<br>

## Построим таблицу для распределения 
<br>

|  | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| P<sub>1</sub> |   |  |  |   |   |   |   |  |   |
| P<sub>2</sub> |   |  |  |   |   |   |   |  |   |

## Расставим приоритеты


|A|B|C|D|
|:-|:---:|:----:|---:| 
|45|19|16|10|
|I|II|III|IV|


Для процесса с самым высоким приоритетом ставим максимально возможное количество самых можнщых исполнителей (так как процес 1, то и исполнитель будет 1), для следующего также.  

|A|B|C|D|
|:-|:---:|:----:|---:| 
|45|19|16|10|
|I|II|III|IV|
|P<sub>1</sub>|P<sub>2</sub>||| 



### Находим время между приоритетами А и В:

```javascript
45 - 7 * t = 1 - 3 * t
26 = 4 * t
t = 26 / 4 
```

### Теперь находим время между приоритетами B и C:

```javascript
B = C
1 - 3 * t = 16
t = 1
```


Минимальное время = 1


<table>
  <tr>
    <th></th>
    <th>1</th>
    <th>2</th>
    <th>3</th>
    <th>4</th>
    <th>5</th>
    <th>6</th>
    <th>7</th>
    <th>8</th>
    <th>9</th>
  </tr>
  <tr>
    <td>P<sub>1</sub></td>
    <td style="text-align: center;">A</td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
  </tr>
  <tr>
    <td>P<sub>2</sub></td>
    <td style="text-align: center;">B</td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
  </tr>
</table>

## Через 1 минуту длительность заданий будет составлять

|A|B|C|D|
|:-|:---:|:----:|---:|
|38|16|16|10|


Как мы видим, приоритеты B и C совпадают.\
Разделим производительность второго исполнителя попалам, поскольку совпадают именно два приоритета.
<table>
  <tr>
    <th>A</th>
    <th>B</th>
    <th>C</th>
    <th>D</th>
  </tr>
  <tr>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
  </tr>
  <tr>
    <td style="text-align: center;" colspan="1">P<sub>1</sub></td>
    <td style="text-align: center;" colspan="2">P'<sub>2</sub> = <sup>3</sup>&frasl;<sub>2</sub></td>
    <td style="text-align: center;" colspan="1"></td>
  </tr>
</table>


Теперь повторим предыдущие вычисления приоритетов, на место двух приоритетов B и C взяв один BC.



### Решим уравнение A = BC:
```javascript
38 - 7 * t = 16 - 1.5 * t
22 = 3.5 * t 
t = 22 / 5.5
t = 4
```

### Решим уравнение BC = D:

```javascript
15 - 1.5 * t = 10
6 = 1.5 * t
t = 6 / 1.5
t = 4
```
Минимальное время = 4

<table>
  <tr>
    <th></th>
    <th>1</th>
    <th>2</th>
    <th>3</th>
    <th>4</th>
    <th>5</th>
    <th>6</th>
    <th>7</th>
    <th>8</th>
    <th>9</th>
  </tr>
  <tr>
    <td>P<sub>1</sub></td>
    <td style="text-align: center;">A</td>
    <td style="text-align: center;" colspan="4">A</td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
    <td style="text-align: center;"></td>
  </tr>
  <tr>
    <td>P<sub>2</sub></td>
    <td style="text-align: center;" >B</td>
    <td style="text-align: center;" colspan="2">B</td>
    <td style="text-align: center;" colspan="2">C</td>
    <td style="text-align: center;" ></td>
    <td style="text-align: center;" ></td>
    <td style="text-align: center;" ></td>
    <td style="text-align: center;" ></td>
  </tr>
</table>


## Через еще 4 минуты длительность заданий будет составлять
Как мы видим, все приоритеты совпадают.\
Разделим производительность обоих исполнителей на 4, поскольку совпадают все 4 приоритета.


<table>
  <tr>
    <th>A</th>
    <th>B</th>
    <th>C</th>
    <th>D</th>
  </tr>
  <tr>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
    <td style="text-align: center;">10</td>
  </tr>
  <tr>
    <td style="text-align: center;" colspan="4">(P<sub>1</sub>P<sub>2</sub>)' = <sup>10</sup>&frasl;<sub>4</sub></td>
  </tr>
</table>


```javascript
10 / 4 = 2.5
10 - 2.5 * t = 0
t = 10 / 2.5
t = 4
```

<table>
  <tr>
    <th></th>
    <th>1</th>
    <th>2</th>
    <th>3</th>
    <th>4</th>
    <th>5</th>
    <th>6</th>
    <th>7</th>
    <th>8</th>
    <th>9</th>
  </tr>
  <tr>
    <td>P<sub>1</sub></td>
    <td style="text-align: center;">A</td>
    <td style="text-align: center;" colspan="4">A</td>
    <td style="text-align: center;">A</td>
    <td style="text-align: center;">B</td>
    <td style="text-align: center;">C</td>
    <td style="text-align: center;">D</td>
  </tr>
  <tr>
    <td>P<sub>2</sub></td>
    <td style="text-align: center;" >B</td>
    <td style="text-align: center;" colspan="2">B</td>
    <td style="text-align: center;" colspan="2">C</td>
    <td style="text-align: center;" >D</td>
    <td style="text-align: center;" >A</td>
    <td style="text-align: center;" >B</td>
    <td style="text-align: center;" >C</td>
  </tr>
</table>
