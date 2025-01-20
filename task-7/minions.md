# Вариант №4

## 1 шаг - построим граф зависимостей
graph TB
A((A))
B((B))
C((C))
F((F))
G((G))
H((H))
I((I))
J((J))
K((K))
L((L))
M((M))
O((O))
B --> J
B --> M
B --> O
L --> J
L --> B
C --> B
I --> B
H --> B
H --> C
K --> C
F --> L
F --> H
A --> F
G --> H
G --> K

## 2 шаг - удалим транзитивные ребра B-H и J-L
graph TB
A((A))
B((B))
C((C))
F((F))
G((G))
H((H))
I((I))
J((J))
K((K))
L((L))
M((M))
O((O))
B --> J
B --> M
B --> O
L --> B
C --> B
I --> B
H --> C
K --> C
F --> L
F --> H
A --> F
G --> H
G --> K

## 3 шаг - построим граф зависимостей с приоритетами
graph TB
A((A #12 <10>))
B((B #4 <3,2,1>))
C((C #6 <4>))
F((F #10 <8,5>))
G((G #11 <9,8>))
H((H #8 <6>))
I((I #7 <4>))
J((J #1 <>))
K((K #9 <6>))
L((L #5 <4>))
M((M #2 <>))
O((O #3 <>))
B --> J
B --> M
B --> O
L --> B
C --> B
I --> B
H --> C
K --> C
F --> L
F --> H
A --> F
G --> H
G --> K

## 4 шаг - построим диаграмму Ганта
gantt
    title Диаграмма Ганта
    dateFormat HH:mm    
    axisFormat %H:%M
    Начало выполнения работ : milestone, m1, 00:00, 0h
    section Исп. 1
    J         :j, 00:00, 1h
    O         :o, after j, 1h    
    B         :b, after j m o, 1h
    L         :l, after b, 1h
    I         :i, after l, 1h
    K         :k, after i, 1h
    G         :g, after h k, 1h
    section Исп. 2
    M         :m, 00:00, 1h
    C         :c, after b, 1h
    H         :h, after c, 1h
    F         :f, after l h, 1h
    A         :a, after f, 1h
    Окончание выполнения работ : milestone, m2, 07:00, 0h

# Ответ
Длительность расписания составляет 7 часов. Расписание предствалено в виде даиграммы Ганта.
