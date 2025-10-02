## Membros
- Guilherme de Abreu – 22.222.028-7  
- Kaique Fernandes – 22.221.011-4  

## Exercício 1 — Caminhos Independentes

### Código

```python
def verificar(n):
    if n > 0:
        if n % 2 == 0:
            return "Par positivo"
        else:
            return "Ímpar positivo"
    elif n < 0:
        return "Negativo"
    else:
        return "Zero"
```

### Grafo 1

<img width="777" height="532" alt="image" src="https://github.com/user-attachments/assets/303353d4-3836-4db9-aa68-b1184635622f" />


### Complexidade Ciclomática

V(G) = 4

### Caminhos Independentes

1.  n > 0 e par
    
2.  n > 0 e ímpar
    
3.  n < 0
    
4.  n == 0
    

### Casos de Teste

CT | n | Esperado  
1 | 2 | Par positivo  
2 | 3 | Ímpar positivo  
3 | -1 | Negativo  
4 | 0 | Zero

## Exercício 2 — Teste de Comando e Ramos

### Código

```python
def classificar(x):
    if x > 100:
        return "Alto"
    if x > 50:
        return "Médio"
    return "Baixo"
```

### Grafo 2

<img width="421" height="510" alt="image" src="https://github.com/user-attachments/assets/da043d9f-146c-4b63-8e03-5c0a146f56d3" />

### Complexidade Ciclomática

V(G) = 3

### Caminhos Independentes

1.  x > 100
    
2.  50 < x <= 100
    
3.  x <= 50
    

### Casos de Teste

CT | x | Esperado  
1 | 120 | Alto  
2 | 75 | Médio  
3 | 10 | Baixo

## Exercício 3 — Teste de Condição

### Código

```python
def acesso(idade, membro):
    if idade >= 18 and membro:
        return "Permitido"
    return "Negado"
```

### Grafo 3

<img width="420" height="531" alt="image" src="https://github.com/user-attachments/assets/5b30c246-129c-44f5-842a-49432245f8e3" />

### Complexidade Ciclomática

V(G) = 2

### Caminhos Independentes

1.  condição verdadeira → Permitido
    
2.  condição falsa → Negado
    

### Casos de Teste

CT | idade | membro | Esperado  
1 | 18 | True | Permitido  
2 | 20 | False | Negado  
3 | 17 | True | Negado  
4 | 17 | False | Negado

## Exercício 4 — Teste de Ciclo (Laço Simples)

### Código

```python
def somar_ate(n):
    soma = 0
    for i in range(n):
        soma += i
    return soma
```

### Grafo 4

<img width="393" height="524" alt="image" src="https://github.com/user-attachments/assets/217ab87c-ebda-47ee-9e95-fcdf0c252154" />

### Complexidade Ciclomática

V(G) = 2

### Caminhos Independentes

1.  laço não executa (n=0)
    
2.  laço executa (n>0)
    

### Casos de Teste

CT | n | Esperado  
1 | 0 | 0  
2 | 1 | 0  
3 | 5 | 10

## Exercício 5 — Teste de Ciclo (Aninhado)

### Código

```python
def multiplicar_matrizes(m, n):
    for i in range(m):
        for j in range(n):
            print(f"Posição ({i}, {j})")
```

### Grafo 5

<img width="326" height="551" alt="image" src="https://github.com/user-attachments/assets/b1f47520-80a4-4485-b5d3-d686ef56e6fc" />

### Complexidade Ciclomática

V(G) = 3

### Caminhos Independentes

1.  m=0 ou n=0 (nenhum print)
    
2.  m>0, n=0 (externo roda, interno não)
    
3.  m>0, n>0 (ambos rodam)
    

### Casos de Teste

CT | m | n | Prints esperados  
1 | 0 | 0 | 0  
2 | 3 | 0 | 0  
3 | 1 | 4 | 4  
4 | 5 | 1 | 5  
5 | 3 | 4 | 12

## Exercício 6 — Teste Completo

### Código

```python
def analisar(numeros):
    total = 0
    for n in numeros:
        if n > 0 and n % 2 == 0:
            total += n
        elif n < 0:
            total -= 1
        else:
            continue
    if total > 10:
        return "Acima"
    return "Abaixo"
```

### Grafo 6

<img width="648" height="643" alt="image" src="https://github.com/user-attachments/assets/d00f758a-4b73-4600-89d0-a4599b48a196" />

### Complexidade Ciclomática

Decisões:

laço for (1)

if (n > 0 and n % 2 == 0) (1)

elif (n < 0) (1)

if (total > 10) (1)

V(G) = 4 + 1 = 5

### Caminhos Independentes (base)

1 | Lista vazia (sem entrar no laço) | total=0 | Retorno: Abaixo 2 | Pelo menos um n positivo e par sem passar de 10 (ex.: \[2\]) | total=2 | Retorno: Abaixo 3 | Positivos pares somando acima de 10 (ex.: \[6, 6\]) | total=12 | Retorno: Acima 4 | Pelo menos um n negativo (ex.: \[-1\]) | total=-1 | Retorno: Abaixo 5 | Zeros/ímpares positivos apenas (ex.: \[0, 3\]) | total=0 | Retorno: Abaixo

### Casos de Teste — Cobertura de Comando e Ramo

CT | Entrada (numeros) | Objetivo (ramo/comando) | Total final | Retorno esperado
1 | [] | laço 0x + if final (false) | 0 | Abaixo
2 | [2] | if composto true → total += n | 2 | Abaixo
3 | [6, 6] | if composto true (várias iterações) + if final (true) | 12 | Acima
4 | [-1] | elif n < 0 → total -= 1 | -1 | Abaixo
5 | [3] | else → continue | 0 | Abaixo

### Casos de Teste — Cobertura da Condição Composta `(n > 0 and n % 2 == 0)`

CT | n | (n > 0) | (n % 2 == 0) | Avaliação da condição | Ramo tomado | Retorno esperado (lista=[n])
C1 | 2 | True | True | True | total += n | Abaixo
C2 | 3 | True | False | False | continue | Abaixo
C3 | -2 | False | True | False | total -= 1 | Abaixo
C4 | -3 | False | False | False | total -= 1 | Abaixo

### Casos de Teste — Comportamentos do Laço

CT | Entrada (numeros) | Iterações do laço | Ações internas | Total final | Retorno esperado
L1 | [] | 0 | — | 0 | Abaixo
L2 | [2] | 1 | total += 2 | 2 | Abaixo
L3 | [6, 6] | 2 | +6, +6 | 12 | Acima

### Observações

A condição composta usa curto-circuito: se n > 0 for False, a verificação de paridade não altera o fluxo (o and já é False).

O continue apenas salta para a próxima iteração, mantendo total inalterado.
