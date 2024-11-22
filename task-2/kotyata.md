# Вычисление ленточного определителя трехдиагональной матрицы (Вариант 2)

Дана трехдиагональная матрица следующего вида:

$$    
A =     
 \begin{pmatrix}    
  2 & 1 & 0 & \cdots & 0 & 0 \\    
  1 & 2 & 1 & \cdots & 0 & 0 \\    
  0 & 1 & 2 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & 2 & 1 \\    
  0 & 0 & 0 & \cdots & 1 & 2     
 \end{pmatrix}    
$$

Необходимо:
1. Вывести рекуррентное соотношение для предложенной матрицы.  
2. Составить и решить характеристическое уравнение.  
3. Вывести формулу общего решения.  
4. Рассчитать на основе полученной формулы значение определителя матрицы порядка 10.  

## Выведение рекуррентного соотношения

Рекуррентное соотношение в общем виде:

$$
\Delta_n = a \cdot \Delta_{n-1} - b \cdot c \cdot \Delta_{n-2}
$$

Из анализа диагональных элементов матрицы следует:
- $a = 2$,
- $b = 1$,
- $c = 1$.

Таким образом, при подстановке значений $a$, $b$ и $c$ получаем следующую формулу:

$$
\Delta_n = 2 \cdot \Delta_{n-1} - \Delta_{n-2}
$$

## Характеристическое уравнение

Записываем характеристическое уравнение:

$$
\lambda^n = 2\cdot \lambda^{n-1} - \lambda^{n-2} 
$$ 

При условии, что $\lambda \neq 0$, сокращаем это уравнение на $\lambda^{n-2}$ :

$$ 
\lambda^2 = 2\lambda - 1 
$$ 

Переносим все значения влево:

$$ 
\lambda^2 - 2\lambda + 1 = 0 
$$ 

Находим корни:

$$ 
(\lambda - 1)^2 = 0 \quad \Rightarrow \quad \lambda_{1,2} = 1 
$$ 

## Общая формула решения

Подставляем корни в общую формулу вида:

$$
\Delta_n = C_1 \cdot n \cdot \lambda^n + C_2 \cdot \lambda^n
$$

При подстановке $\lambda = 1$ получаем:

$$
\Delta_n = C_1 \cdot n + C_2 \qquad (1)
$$

Из представленной матрицы следует, что $ \Delta_1 = 2 $ и $ \Delta_2 = 3 $. Составим систему из уравнений *(1)* для нахождения $C_1$ и $C_2$:

$$
\begin{cases}
C_1 \cdot 1 + C_2 = 2 & (2) \\ 
C_1 \cdot 2 + C_2 = 3 & (3)
\end{cases}
$$ 

Из уравнения *(2)* выразим $C_2$:

$$
C_2 = 2 - C_1
$$ 

Подставим это значение в уравнение *(3)*:

$$
2 \cdot C_1 + (2 - C_1) = 3 \quad  \Rightarrow \quad 2 \cdot C_1 - C_1 + 2 = 3 \quad  \Rightarrow\\ 
\Rightarrow \quad C_1 = 1
$$

Найденное значение $C_1$ подставляем в *(2)*:

$$
1 + C_2 = 2 \quad\Rightarrow \quad C_2 = 1 
$$

Таким образом, общая формула для нахождения определителя *n*-го порядка представленной матрицы имеет следующий вид:

$$
\Delta_n = n + 1 \qquad (4)
$$

## Расчет значения определителя 

По формуле *(4)*, найдем определитель матрицы порядка 10:

$$
\Delta_{10} = 10 + 1 = 11
$$