---
marp: true
theme: default
paginate: true
---

# CB0589 ÁLGEBRA LINEAR

## Álgebra de Matrizes e Invertibilidade

<style>
.katex { font-size: 1.1em !important; }
</style>

---

## **O que é uma Matriz?**

Uma matriz é um arranjo retangular de números, símbolos ou expressões, organizados em linhas e colunas.

**Representação:**
Uma matriz $A$ com $m$ linhas e $n$ colunas (ordem $m \times n$) é representada como:

$$
A = (a_{ij})_{m \times n} =
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}
\end{bmatrix}
$$

O elemento $a_{ij}$ está na linha $i$ e na coluna $j$.

---

## **Definição: Adição e Subtração de Matrizes**

Sejam $A=(a_{ij})$ e $B=(b_{ij})$ duas matrizes de mesma ordem $m \times n$.

- A **soma** $A+B$ é a matriz $C=(c_{ij})$ de ordem $m \times n$ onde cada elemento é a soma dos elementos correspondentes:
  $$c_{ij} = a_{ij} + b_{ij}$$

- A **diferença** $A-B$ é definida de forma análoga:
  $$(A - B)_{ij} = a_{ij} - b_{ij}$$

---

### Exemplo: Adição e Subtração

Sejam
$$
A=\begin{bmatrix}1&2\\3&4\end{bmatrix},\quad
B=\begin{bmatrix}5&6\\7&8\end{bmatrix}
$$

**Soma:**
$$
A+B=\begin{bmatrix}1+5&2+6\\3+7&4+8\end{bmatrix}
=\begin{bmatrix}6&8\\10&12\end{bmatrix}
$$

**Subtração:**
$$
A-B=\begin{bmatrix}1-5&2-6\\3-7&4-8\end{bmatrix}
=\begin{bmatrix}-4&-4\\-4&-4\end{bmatrix}
$$

---

## **Definição: Multiplicação por Escalar**
<br>

Seja $A=(a_{ij})$ uma matriz de ordem $m \times n$ e $k$ um número real (escalar).

<br>

- O **produto por escalar** $kA$ é a matriz $C=(c_{ij})$ de ordem $m \times n$ onde cada elemento é o produto do elemento correspondente de $A$ pelo escalar $k$:
  $$c_{ij} = k \cdot a_{ij}$$

---

### Exemplo: Multiplicação por Escalar

Seja a matriz $A$ e o escalar $k = 3$:
$$
A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}
$$

**Multiplicação ($k A$):**
$$
3A = \begin{bmatrix} 3 \cdot 1 & 3 \cdot 2 \\ 3 \cdot 3 & 3 \cdot 4 \end{bmatrix} = \begin{bmatrix} 3 & 6 \\ 9 & 12 \end{bmatrix}
$$

---

## **Definição: Multiplicação de Matrizes**

Seja $A=(a_{ij})$ uma matriz de ordem $m \times n$ e $B=(b_{ij})$ de ordem $n \times p$.

- O **produto** $AB$ é a matriz $C=(c_{ij})$ de ordem $m \times p$.
- O elemento $c_{ij}$ é obtido pela soma dos produtos dos elementos da linha $i$ de $A$ pelos elementos da coluna $j$ de $B$:
  $$c_{ij} = \sum_{k=1}^{n} a_{ik}b_{kj}$$

**Atenção:** O número de colunas da primeira matriz deve ser igual ao número de linhas da segunda.

---

### Exemplo: Multiplicação de Matrizes

<br>

$$
A_{2 \times 2} = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}, \quad B_{2 \times 2} = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}
$$
$$
C = AB = \begin{bmatrix} (1\cdot5+2\cdot7) & (1\cdot6+2\cdot8) \\ (3\cdot5+4\cdot7) & (3\cdot6+4\cdot8) \end{bmatrix} = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
$$

<br>

**A multiplicação de matrizes NÃO é comutativa!**
<br>
$$
BA = \begin{bmatrix} (5\cdot1+6\cdot3) & (5\cdot2+6\cdot4) \\ (7\cdot1+8\cdot3) & (7\cdot2+8\cdot4) \end{bmatrix} = \begin{bmatrix} 23 & 34 \\ 31 & 46 \end{bmatrix} \neq AB
$$

---

## **Matriz × Vetor (coluna única)**

Se $A=[\,a_1\ \cdots\ a_n\,]\in\mathbb{R}^{m\times n}$ e $x=\begin{bmatrix}x_1\\ \vdots\\ x_n\end{bmatrix}\in\mathbb{R}^n$, então
$$
Ax=\sum_{k=1}^n x_k\,a_k \;\in\; \mathbb{R}^m,
$$
isto é, **$Ax$ é combinação linear das colunas** de $A$ com pesos dados pelas entradas de $x$.

---


###  Exemplo: 
<br>

**Dimensões:** $A\in\mathbb{R}^{m\times n}$, $x\in\mathbb{R}^n \Rightarrow Ax\in\mathbb{R}^m$.

<br>

$$
A=\begin{bmatrix}1&2\\3&4\\5&6\end{bmatrix},\quad
x=\begin{bmatrix}2\\-1\end{bmatrix}
\Rightarrow\ 
Ax=2\!\begin{bmatrix}1\\3\\5\end{bmatrix}-1\!\begin{bmatrix}2\\4\\6\end{bmatrix}
=\begin{bmatrix}0\\2\\4\end{bmatrix}.
$$


---

## **Vetor (linha única) × Matriz**

<br>

Se $y=\begin{bmatrix}y_1&\cdots&y_m\end{bmatrix}\in\mathbb{R}^{1\times m}$ e $A\in\mathbb{R}^{m\times n}$,
<br>

$$
y A=\sum_{i=1}^m y_i\,(\text{linha } i \text{ de } A) \;\in\; \mathbb{R}^{1\times n},
$$
<br>

isto é, **$yA$ é combinação linear das linhas** de $A$ com pesos dados pelas entradas de $y$.

---

### Exemplo:  
<br>

**Dimensões:** $y\in\mathbb{R}^{1\times m}$, $A\in\mathbb{R}^{m\times n} \Rightarrow yA\in\mathbb{R}^{1\times n}$.

<br>

$$
y=\begin{bmatrix}1&-2&0\end{bmatrix},\ 
A=\begin{bmatrix}1&2\\3&4\\5&6\end{bmatrix}
\Rightarrow\ 
y A=1\!\begin{bmatrix}1&2\end{bmatrix}-2\!\begin{bmatrix}3&4\end{bmatrix}
=\begin{bmatrix}-5&-6\end{bmatrix}.
$$



---

## **Interpretação do Produto: Combinação de Colunas**
<br>

Se $A\in\mathbb{R}^{m\times n}$ e $B=[\,b_1\ \cdots\ b_p\,]\in\mathbb{R}^{n\times p}$ com $b_j$ colunas,
<br>

$$
AB=\big[\,A b_1\ \cdots\ A b_p\,\big],\qquad
A b_j=\sum_{k=1}^{n} b_{kj}\, a_k,
$$
<br>

onde $a_k$ é a $k$-ésima **coluna** de $A$.

---

### Exemplo:  
$$
A=\begin{bmatrix}1&0\\[2pt]2&1\\[2pt]0&1\end{bmatrix},\
B=\begin{bmatrix}2&-1\\[2pt]3&4\end{bmatrix}
\Rightarrow
a_1=\begin{bmatrix}1\\2\\0\end{bmatrix},\ a_2=\begin{bmatrix}0\\1\\1\end{bmatrix}
$$

$$
AB=\big[\,2a_1+3a_2\ \ \ -a_1+4a_2\,\big]
=\begin{bmatrix}2&-1\\[2pt]7&2\\[2pt]3&4\end{bmatrix}.
$$

---

## **Interpretação do Produto: Combinação de Linhas**

Se $A=\begin{bmatrix}a_{1*}\\ \vdots\\ a_{m*}\end{bmatrix}$ (com $a_{i*}$ a **linha** $i$ de $A$) e $B$ tem linhas $B_{k*}$,
$$
(AB)_{i*}=a_{i*}B=\sum_{k=1}^{n} a_{ik}\, B_{k*}.
$$

---

### Exemplo ( mesmos $A,B$ ):  
Linhas de $B$:
$
B_{1*}=\begin{bmatrix}2&-1\end{bmatrix},\
B_{2*}=\begin{bmatrix}3&4\end{bmatrix}.
$

$
\begin{aligned}
(AB)_{1*}&= [1\ \ 0]\ B=1\cdot B_{1*}+0\cdot B_{2*}=\begin{bmatrix}2&-1\end{bmatrix},\\
(AB)_{2*}&= [2\ \ 1]\ B=2\,B_{1*}+1\,B_{2*}=\begin{bmatrix}7&2\end{bmatrix},\\
(AB)_{3*}&= [0\ \ 1]\ B=0\cdot B_{1*}+1\cdot B_{2*}=\begin{bmatrix}3&4\end{bmatrix}.
\end{aligned}
$
Logo,
$
AB=\begin{bmatrix}2&-1\\[2pt]7&2\\[2pt]3&4\end{bmatrix}.
$

---

## **Definição: Matriz Transposta**

Seja $A=(a_{ij})$ uma matriz de ordem $m \times n$.

<br>

- A **matriz transposta** de $A$, denotada por $A^T$, é a matriz de ordem $n \times m$ obtida pela troca de linhas por colunas:
<br>
$$(A^T)_{ij} = a_{ji}$$

---

### Exemplo: Matriz Transposta

$$
A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} \implies A^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}
$$

**Propriedades:**
- $(A^T)^T = A$
- $(A + B)^T = A^T + B^T$
- $(kA)^T = k A^T$
- $(AB)^T = B^T A^T$

---

## **Definição: Matriz Identidade e Inversa**

**Matriz Identidade ($I_n$):**
É a matriz quadrada de ordem $n$ que é o elemento neutro da multiplicação:
<br>
$$AI_n = I_n A = A$$
<br>
$$ (I_n)_{ij} = \delta_{ij} = \begin{cases} 1 & \text{se } i=j \\ 0 & \text{se } i \neq j \end{cases} $$

---

## **Definição: Matriz Inversa ($A^{-1}$)**

Uma matriz quadrada $A$ de ordem $n$ é **invertível** (ou não singular) se existe uma única matriz $A^{-1}$ de ordem $n$ tal que:
<br>
$$A A^{-1} = A^{-1} A = I_n$$
<br>

Se tal matriz $A^{-1}$ não existe, $A$ é dita **não invertível** (ou singular). Uma condição necessária e suficiente para $A$ ser invertível é que $\det(A) \neq 0$.

---

## **Teoremas e Propriedades da Matriz Inversa**

Para matrizes $A$ e $B$ invertíveis de mesma ordem $n$, e um escalar $k \neq 0$:

1.  **Unicidade da Inversa:** Se uma matriz tem inversa, ela é única.
<br>
2.  **Inversa de um Produto:** O produto $AB$ também é invertível, e sua inversa é:
    $$(AB)^{-1} = B^{-1}A^{-1}$$
<br>

3.  **Inversa da Transposta:** A transposta de uma matriz invertível também é invertível, e sua inversa é:
    $$(A^T)^{-1} = (A^{-1})^T$$

---

4.  **Inversa da Inversa:** A inversa da inversa de uma matriz é a própria matriz:
    $$(A^{-1})^{-1} = A$$ 
    <br>
5.  **Inversa de um Múltiplo Escalar:** A matriz $kA$ é invertível, e sua inversa é:
    $$(kA)^{-1} = \frac{1}{k}A^{-1}$$

---

### Exemplo: Identidade e Inversa

A identidade de ordem 2 é $I_2 = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$.

Dada a matriz $A = \begin{bmatrix} 2 & 5 \\ 1 & 3 \end{bmatrix}$, sua inversa é $A^{-1} = \begin{bmatrix} 3 & -5 \\ -1 & 2 \end{bmatrix}$.

**Verificação:**
$$
AA^{-1} = \begin{bmatrix} 2 & 5 \\ 1 & 3 \end{bmatrix} \begin{bmatrix} 3 & -5 \\ -1 & 2 \end{bmatrix} = \begin{bmatrix} (6-5) & (-10+10) \\ (3-3) & (-5+6) \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} = I_2
$$

---

## **Definição: Matrizes Especiais**

Uma matriz quadrada $A = (a_{ij})$ é dita:
- **Diagonal:** se $a_{ij} = 0$ para todo $i \neq j$.
- **Triangular Superior:** se $a_{ij} = 0$ para todo $i > j$.
- **Triangular Inferior:** se $a_{ij} = 0$ para todo $i < j$.
- **Simétrica:** se $A = A^T$, ou seja, $a_{ij} = a_{ji}$ para todos $i, j$.
- **Ortogonal:** se sua inversa é sua transposta, $A^{-1} = A^T$.

---

### Exemplos de Matrizes Especiais

$$
\begin{array}{r \;\; c}
\textbf{Diagonal:} &
\begin{bmatrix}
2 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 5
\end{bmatrix} \\[1.2em]

\textbf{Triangular Superior:} &
\begin{bmatrix}
1 & 3 & 9 \\
0 & 4 & -2 \\
0 & 0 & 8
\end{bmatrix} \\[1.2em]

\textbf{Simétrica:} &
\begin{bmatrix}
1 & 7 & 3 \\
7 & 4 & -5 \\
3 & -5 & 6
\end{bmatrix}
\end{array}
$$


---

### Exercícios Práticos

**Dadas as matrizes:**
$$
A = \begin{bmatrix} 1 & 0 \\ 2 & 3 \end{bmatrix}, \quad B = \begin{bmatrix} -1 & 4 \\ 1 & 2 \end{bmatrix}, \quad C = \begin{bmatrix} 3 & -1 & 0 \\ 2 & 5 & -4 \end{bmatrix}
$$

**Calcule (se possível):**
1. $A + B$
2. $3A - 2B$
3. $AB$ e $BA$
4. $AC$
5. $C^T$
6. $(A + B)^T$ e $A^T + B^T$


---
## **Respostas dos Exercícios**

1.  $A + B = \begin{bmatrix} 0 & 4 \\ 3 & 5 \end{bmatrix}$ 
<br>
2.  $3A - 2B = \begin{bmatrix} 5 & -8 \\ 4 & 5 \end{bmatrix}$
<br>
3.  $AB = \begin{bmatrix} -1 & 4 \\ 1 & 14 \end{bmatrix}$, $BA = \begin{bmatrix} 7 & 12 \\ 5 & 6 \end{bmatrix}$

--- 

4.  $AC = \begin{bmatrix} 3 & -1 & 0 \\ 12 & 13 & -12 \end{bmatrix}$
<br>
5.  $C^T = \begin{bmatrix} 3 & 2 \\ -1 & 5 \\ 0 & -4 \end{bmatrix}$
<br>
6.  $(A + B)^T = \begin{bmatrix} 0 & 3 \\ 4 & 5 \end{bmatrix}$, $A^T + B^T = \begin{bmatrix} 0 & 3 \\ 4 & 5 \end{bmatrix}$