# Оптимизация расписания работ для исполнителей (ВАРИАНТ 7)

4 НЕЗАВИСИМЫХ ЗАДАЧИ:
| A  | B  | C  | D  | 
|----|----|----|----|
| 54 | 45 | 18 | 18 |

2 ПРОИЗВОДИТЕЛЯ:
| P1 | P2 |
|----|----|
| 4  | 3  |

ОБЩЕЕ ВРЕМЯ РАБОТ:
t_min = 54 + 45 + 18 + 18 / 4 + 3 = 20

Чтобы составить оптимальное расписание работ, воспользуемся алгоритмом Джонсона с приоритетами задач.

1. Расставить приоритеты на задачи и назначить исполнителя:

| Задача | Длительность | Приоритет | Исполнитель |
|--------|--------------|-----------|-------------|
| A      | 54           | I         | P1          |
| B      | 45           | II        | P1          |
| C      | 18           | III       | P2          |
| D      | 18           | III       | P2          |


2. Определить, какое событие наступит раньше, и сколько времени это займет:

| AB | ``` 54 - 4t = 45 - 3t => t = 9```
| BCD | ```45 - 9t = 18 => t = 9```

Через 9 сек задача A станет равна B, C и D = 18.

3. Расчитать работы через 9 сек:

| Задача | Длительность | Приоритет | Исполнитель |
|--------|--------------|-----------|-------------|
| A      | 18           | I         | P1 + P2     |
| B      | 18           | I         | P1 + P2     |
| C      | 18           | I         | P1 + P2     |
| D      | 18           | I         | P1 + P2     |

ЗАДАЧА СВОДИТСЯ К РАВНОМЕРНОМУ РАСПРЕДЕЛЕНИЮ.

РАБОТЫ МЕЖДУ ИСПОЛЬНИТЕЛЯМИ:

| P1 | P2 |
|----|----|
| A  | D  | 
| B  | A  | 
| C  | B  | 
| D  | C  | 

4. Ищем необходимое время:

```markdown
18 + 18 + 18 + 18 / 4 + 3 = 72  /7 ≈ 10.2 ≈ 11
```
ИТОГОВОЕ ВРЕМЯ: 
```markdown
11 + 9 = 20 (t_min)
```

ОТВЕТ: Длительность оптимального расписания составляет 20 сек. 

Расписание в диаграмме Ганта: 

```mermaid
gantt
    title Диаграмма Ганта
    dateFormat  DD HH:mm
    axisFormat %H:%M
    Начало : milestone, m1, 01 00:00, 0h

    section P1
    A  :a1, 01 00:00, 9h
    B  :a2, after a1, 2h
    B  :a3, after a2, 2h
    C  :a4, after a3, 2h
    D  :a5, after a4, 2h

    section P2
    B  :b1, 01 00:00, 9h
    D  :b2, after b1, 2h
    A  :b3, after b2, 2h
    B  :b4, after b3, 2h
    C  :b5, after b4, 2h

    Окончание : milestone, m2, 01 09:00, 0h
```

