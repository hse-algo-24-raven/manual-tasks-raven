# Задача о назначениях. Венгерский алгоритм.

Для выполнения задания необходимо: 
1. Решить задачу о назначениях с использованием Венгерского алгоритма.
2. Оформить решение задачи по шагам с подробными комментариями, таблицами и диаграммами.
3. В ответе указать минимальную сумму затрат на выполнение всех заданий.
4. В ответе вывести найденные назначения


**Решение должно содержать номер варианта и подробное пошаговое описание.**


### Вариант 1:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  9    |   7   |  16   |   9   |  12   |
| **B** |  14   |   5   |  10   |  14   |   7   |
| **C** |  11   |   18  |  18   |  10   |  10   |
| **D** |  10   |   5   |  10   |  14   |  19   |
| **E** |  11   |   6   |  5    |   8   |   9   |

### Вариант 2:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  19   |  19   |  14   |  10   |  14   |
| **B** |  17   |  18   |  11   |  16   |  11   |
| **C** |  13   |   5   |  18   |  20   |  10   |
| **D** |  14   |   5   |   9   |  12   |  20   |
| **E** |  15   |   7   |  14   |   8   |  16   |

### Вариант 3:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |   9   |   7   |  16   |   9   |  12   |
| **B** |  14   |   5   |  10   |  14   |   7   |
| **C** |  11   |  18   |  18   |  10   |  10   |
| **D** |  10   |   5   |  10   |  14   |  19   |
| **E** |  11   |   6   |   5   |   8   |   9   |

### Вариант 4:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  19   |  10   |   9   |  10   |   7   |
| **B** |  13   |   5   |   5   |   5   |  18   |
| **C** |   7   |  11   |   9   |  11   |  14   |
| **D** |   5   |  13   |  16   |  20   |  17   |
| **E** |  12   |  20   |  20   |  13   |   7   |


### Вариант 5:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  19   |  19   |  14   |  10   |  14   |
| **B** |  17   |  18   |  11   |  16   |  11   |
| **C** |  13   |   5   |  18   |  20   |  10   |
| **D** |  14   |   5   |   9   |  12   |  20   |
| **E** |  15   |   7   |  14   |   8   |  16   |

### Вариант 6:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |   8   |  15   |  16   |  17   |  20   |
| **B** |   8   |  10   |   9   |  13   |  15   |
| **C** |   6   |  10   |  14   |  11   |   7   |
| **D** |  18   |  11   |  11   |  11   |  11   |
| **E** |   5   |  19   |  14   |   5   |   8   |

### Вариант 7:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  13   |  19   |   8   |  16   |   5   |
| **B** |   9   |  14   |   7   |  10   |  10   |
| **C** |  10   |  20   |   6   |   5   |  10   |
| **D** |  18   |  13   |   9   |  12   |  17   |
| **E** |  13   |  15   |  17   |  17   |  19   |

### Вариант 8:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  11   |  20   |  20   |   8   |  12   |
| **B** |  17   |   9   |  13   |   5   |   8   |
| **C** |   6   |   7   |  16   |  20   |   9   |
| **D** |  18   |  20   |   6   |   9   |   7   |
| **E** |  16   |  15   |  18   |  11   |   9   |

### Вариант 9:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |  15   |  12   |  14   |  10   |  12   |
| **B** |  19   |  11   |   7   |  19   |  16   |
| **C** |   6   |  14   |   9   |  19   |  20   |
| **D** |  12   |  13   |   9   |  19   |  13   |
| **E** |  10   |  14   |  11   |  15   |  18   |

### Вариант 10:
#### Матрица затрат:

|       | **1** | **2** | **3** | **4** | **5** |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| **A** |   8   |  15   |  14   |  12   |  11   |
| **B** |   5   |  12   |  18   |   5   |  11   |
| **C** |  13   |   5   |   6   |  15   |   6   |
| **D** |  13   |  13   |   7   |  11   |  10   |
| **E** |  15   |  15   |  10   |  17   |  20   |
