```python
import numpy as np
import time
```

---

# Desempenho: Numpy x Python


```python
tamanho = 1000000
```


```python
# Python

lista_python = []
lista_python = [x for x in range(tamanho)]
print(lista_python[:10])
print(lista_python[-10:])
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [999990, 999991, 999992, 999993, 999994, 999995, 999996, 999997, 999998, 999999]
    


```python
tempo_inicio = time.process_time()
lista_python_mult = [x * 99 for x in lista_python]
tempo_final = time.process_time() - tempo_inicio
tempo_final
```




    0.109375




```python
print(lista_python_mult[:10])
print(lista_python_mult[-10:])
```

    [0, 99, 198, 297, 396, 495, 594, 693, 792, 891]
    [98999010, 98999109, 98999208, 98999307, 98999406, 98999505, 98999604, 98999703, 98999802, 98999901]
    


```python
# Numpy

numpy_array = np.array(lista_python)
print(numpy_array[:10])
print(numpy_array[-10:])
```

    [0 1 2 3 4 5 6 7 8 9]
    [999990 999991 999992 999993 999994 999995 999996 999997 999998 999999]
    


```python
tempo_inicio_np = time.process_time()
numpy_array_mult = numpy_array * 99
tempo_final_np = time.process_time() - tempo_inicio_np
print(tempo_final_np)
```

    0.03125
    


```python
tempo_final / tempo_final_np
```




    3.5



---


```python
# Criando um Array com Numpy

lista = [1, 2, 3]
np_array = np.array(lista)
np_array
```




    array([1, 2, 3])




```python
# N-Dimensional Array
type(np_array)
```




    numpy.ndarray




```python
# Criando uma Matriz
matriz = [[1, 2, 3], [3, 2, 1], [2, 1, 3]]

print(np.matrix(matriz))
print(type(np.matrix(matriz)))
print('-------------------------')
print(np.array(matriz))
print(type(np.array(matriz)))
```

    [[1 2 3]
     [3 2 1]
     [2 1 3]]
    <class 'numpy.matrix'>
    -------------------------
    [[1 2 3]
     [3 2 1]
     [2 1 3]]
    <class 'numpy.ndarray'>
    

### Arrays e suas dimensões


```python
# 1 dimensão
np.array([1, 2, 3])
```




    array([1, 2, 3])




```python
# 2 dimensões
np.array([[1, 2, 3], [4, 5, 6]])
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
# 3 dimensões
np.array([[[1, 2, 3], [4, 5, 6], [7, 8, 9]],
         [[10, 11, 12], [13, 14, 15], [16, 17, 18]]])
```




    array([[[ 1,  2,  3],
            [ 4,  5,  6],
            [ 7,  8,  9]],
    
           [[10, 11, 12],
            [13, 14, 15],
            [16, 17, 18]]])



### Criando Arrays utilizando range()


```python
# Listas do Python
lista_range = list(range(9))

print(lista_range)
print(type(lista_range))
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8]
    <class 'list'>
    


```python
# Array do Numpy
array_range = np.array(range(9))

print(array_range)
print(type(array_range))
```

    [0 1 2 3 4 5 6 7 8]
    <class 'numpy.ndarray'>
    


```python
# Array do Numpy com intervalo estabelecido
array_intervalado = np.arange(1, 100, 2)

print(array_intervalado)
print(type(array_intervalado))
```

    [ 1  3  5  7  9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45 47
     49 51 53 55 57 59 61 63 65 67 69 71 73 75 77 79 81 83 85 87 89 91 93 95
     97 99]
    <class 'numpy.ndarray'>
    


```python
# Array do Numpy utilizando o número 0
array_zeros = np.zeros(5)
print(array_zeros)
print(type(array_zeros))

print('----------------------------')

# Verificando qual é o tipo dos números dentro do Array
print(array_zeros[0])
print(type(array_zeros[0]))

print('----------------------------')

# Criando Matrizes com Numpy com o número 0
matriz_zeros = np.zeros((3, 3))
print(matriz_zeros)
print(type(matriz_zeros))
```

    [0. 0. 0. 0. 0.]
    <class 'numpy.ndarray'>
    ----------------------------
    0.0
    <class 'numpy.float64'>
    ----------------------------
    [[0. 0. 0.]
     [0. 0. 0.]
     [0. 0. 0.]]
    <class 'numpy.ndarray'>
    


```python
# Arrays do Numpy utilizando o número 1
array_um = np.ones(6)

print(array_um)
print(type(array_um))

print('----------------------------')

# Criando Matrizes com Numpy com o número 0
matriz_um = np.ones((3, 4))
print(matriz_um)
print(type(matriz_um))
print(matriz_um[0, 2])
```

    [1. 1. 1. 1. 1. 1.]
    <class 'numpy.ndarray'>
    ----------------------------
    [[1. 1. 1. 1.]
     [1. 1. 1. 1.]
     [1. 1. 1. 1.]]
    <class 'numpy.ndarray'>
    1.0
    

### Criando Arrays utilizando linspace()


```python
# Arrays com linspace()
np.linspace(1, 10, 15)
```




    array([ 1.        ,  1.64285714,  2.28571429,  2.92857143,  3.57142857,
            4.21428571,  4.85714286,  5.5       ,  6.14285714,  6.78571429,
            7.42857143,  8.07142857,  8.71428571,  9.35714286, 10.        ])



### Matrizes Identidade


```python
np.eye(4)
```




    array([[1., 0., 0., 0.],
           [0., 1., 0., 0.],
           [0., 0., 1., 0.],
           [0., 0., 0., 1.]])



### Criando Arrays com determinada forma e valores aleatórios


```python
# Array com números aleatórios entre 0 e 1
np.random.rand(3)
```




    array([0.89915849, 0.04567777, 0.71857592])




```python
# Matriz com números aleatórios entre 0 e 1
np.random.rand(3,4)
```




    array([[0.96931874, 0.22349373, 0.20041451, 0.2052522 ],
           [0.9195253 , 0.01906233, 0.23637168, 0.83979822],
           [0.87141144, 0.1391494 , 0.82243781, 0.90659137]])




```python
# Array com números aleatórios entre 0 e 1
np.random.random((3, 3))
```




    array([[0.12912382, 0.05850817, 0.53418386],
           [0.37515338, 0.47742372, 0.97231925],
           [0.43068635, 0.94892604, 0.83830592]])




```python
# Array com números aleatórios (Distribuição Normal - Gaussiana)
np.random.randn(10)

# Média de 0 e desvio padrão de 1
```




    array([-0.14291182, -0.68626335,  2.21108046, -0.43395506, -0.64800952,
           -0.62779023, -0.07815792, -0.142069  , -0.75682694, -0.85526432])




```python
# Matriz com números aleatórios (Distribuição Normal - Gaussiana)
np.random.randn(3, 3)
```




    array([[ 0.18494991, -0.85784148, -0.69470006],
           [-1.41559112, -0.98343977,  1.36212512],
           [ 1.13672051,  0.10911294,  0.08371962]])




```python
# Pseudo números aleatórios
np.random.seed(3) 
# colocando o seed eu consigo compartilhar meu notebook que os valores aleatórios de quem for testar serão os mesmos

np.random.randint(25, size=(3, 3))
```




    array([[10, 24,  3],
           [24,  8,  0],
           [21, 19, 10]])



### Números aleatórios entre intervalo estabelecido


```python
np.random.randint(15, 30, 5)
```




    array([26, 24, 24, 25, 20])



### Alterando a forma dos Arrays


```python
array_normal = np.arange(15)
array_normal
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14])




```python
array_normal.reshape(3, 5)
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])




```python
array_rand = np.random.randint(1, 100, 20)
print(f"""Antes:
{array_rand}

Depois: 
{array_rand.reshape(4, 5)}

Mais uma opção:
{np.random.randint(1, 100, size=(4, 5))}""")
```

    Antes:
    [39 97 21 45 94 40 15 27 82 91 23 67  3 64 61  2 52 91 70 98]
    
    Depois: 
    [[39 97 21 45 94]
     [40 15 27 82 91]
     [23 67  3 64 61]
     [ 2 52 91 70 98]]
    
    Mais uma opção:
    [[30 25 63  8 44]
     [34 80 49 38 21]
     [95 50 22 79 29]
     [55  1 65 19 64]]
    


```python
# Para pegar o maior número dentro de um Array
print(f'O maior número é: {array_rand.max()}\nEstá localizado na posição: {array_rand.argmax()}')
```

    O maior número é: 98
    Está localizado na posição: 19
    


```python
# Para pegar o menor número dentro de um Array
print(f'O menor número é: {array_rand.min()}\nEstá localizado na posição: {array_rand.argmin()}')
```

    O menor número é: 2
    Está localizado na posição: 15
    


```python
# Para colocar o array em ordem crescente
cres = array_rand.reshape(4, 5)

print(cres)
print()

print("Para colocar em ordem crescente por linha:")
print(np.sort(cres))
print(f"\nShape: {cres.shape}")

print("\nPara inverter a ordem do array:")
print(cres[::-1])
```

    [[39 97 21 45 94]
     [40 15 27 82 91]
     [23 67  3 64 61]
     [ 2 52 91 70 98]]
    
    Para colocar em ordem crescente por linha:
    [[21 39 45 94 97]
     [15 27 40 82 91]
     [ 3 23 61 64 67]
     [ 2 52 70 91 98]]
    
    Shape: (4, 5)
    
    Para inverter a ordem do array:
    [[ 2 52 91 70 98]
     [23 67  3 64 61]
     [40 15 27 82 91]
     [39 97 21 45 94]]
    

---

### Indexing


```python
indexing = np.arange(0, 21)
indexing
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20])




```python
parte_indexing = indexing[:11].copy()
parte_indexing
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])




```python
parte_indexing[:] = 111
```


```python
parte_indexing
```




    array([111, 111, 111, 111, 111, 111, 111, 111, 111, 111, 111])




```python
indexing
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20])




```python
# Indexing com Array 2D
array_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
array_2d
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
array_2d[:2, :2]
```




    array([[1, 2],
           [4, 5]])



### Seleção condicional


```python
# Retornando valores tipo bool em uma Matriz
array_2d > 3
```




    array([[False, False, False],
           [ True,  True,  True],
           [ True,  True,  True]])




```python
# Retornando valores tipo bool em um Array tradicional
indexing >= 10
```




    array([False, False, False, False, False, False, False, False, False,
           False,  True,  True,  True,  True,  True,  True,  True,  True,
            True,  True,  True])




```python
# Retornando os valores numéricos com seleção condicional
indexing[indexing < 4]
```




    array([0, 1, 2, 3])



### Encontrando valores únicos em uma Matriz/Array


```python
np.unique(array_2d)
```




    array([1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
np.unique(parte_indexing)
```




    array([111])



### Cálculos com Arrays


```python
mat_1 = np.random.randint(0, 15, 5)
mat_1
```




    array([5, 8, 8, 7, 5])




```python
uns = np.ones(5)
uns
```




    array([1., 1., 1., 1., 1.])




```python
# Soma
mat_1 + uns
```




    array([6., 9., 9., 8., 6.])




```python
# Divisão
uns / mat_1
```




    array([0.2       , 0.125     , 0.125     , 0.14285714, 0.2       ])




```python
# Multiplicação
mat_1 * 3
```




    array([15, 24, 24, 21, 15])




```python
# Subtração
mat_1 - 5
```




    array([0, 3, 3, 2, 0])




```python
# Potenciação
mat_1 ** 2
```




    array([25, 64, 64, 49, 25], dtype=int32)




```python
# Média
np.mean(mat_1)
```




    6.6




```python
# Maior número
np.max(mat_1)
```




    8




```python
# Menor número
np.min(mat_1)
```




    5




```python
# Seno
np.sin(mat_1)
```




    array([-0.95892427,  0.98935825,  0.98935825,  0.6569866 , -0.95892427])




```python
# Cosseno
np.cos(mat_1)
```




    array([ 0.28366219, -0.14550003, -0.14550003,  0.75390225,  0.28366219])




```python
# Tangente
np.tan(mat_1)
```




    array([-3.38051501, -6.79971146, -6.79971146,  0.87144798, -3.38051501])



### Desvio Padrão e Variância

**Variância:** é útil para determinar o afastamento da média que os dados de um conjunto analisado apresentam. 
Para isso, Determina-se o valor médio das diferenças quadradas da média.

**Desvio Padrão:** é calculado a partir da variância, pois é raiz quadrada desse parâmetro.

**Fonte:** *https://www.todamateria.com.br/variancia-e-desvio-padrao/*


```python
# Variância

np.var(mat_1)
```




    1.8399999999999999




```python
# Desvio Padrão
np.std(mat_1)
```




    1.3564659966250536




```python
# Tirando a raiz quadrada da Variância para conferir se o valor do desvio padrão está correto
np.sqrt(np.var(mat_1))
```




    1.3564659966250536




```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
