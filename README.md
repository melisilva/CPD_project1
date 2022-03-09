## Trabalho Prático

### Descrição

A ideia é usar primeiro C e fazer assim e depois escolher outra linguagem e verificar se os problemas que existem em C existem também nessa linguagem ou não. Por outro lado, tentar perceber o porquê deste impacto, para o qual utlizaremos Performance API (PAPI).

PAPI corre em Linux. Só precisamos do compilador de C, supostamente. Para a outra linguagem, podemos usar o que acharmos melhor, por exemplo em Windows. Procura-se ver os contadores mais adequados.

Primeira versão é como está, segunda é trocar as duas linhas no ciclo, a terceira é o algoritmo em blocos.

### Notas

Na primeira versão, estamos sempre a acumular tudo no mesmo elemento, acedendo sempre às mesmas colunas repetidamente. Segue a forma como é feita na álgebra. Depois de todos os *k* para um igual *i* e *j*, sobe o *j* em 1 e só depois o *i.* 

Com $i = 0$, $j = 0$ e $k = n - 1$:

$$
C(0, 0) = A(0, n - 1)*B(n-1, 0)
$$

$$
C(i, j) \text { } += A(i, k) * B(k, j)
$$

Percorre-se, portanto, a matriz ao longo da coluna. $O(n) = 2n^3$. Vai precisar-se do triplo do espaço para uma só matriz: primeira matriz, segunda matriz e a matriz resultado.

Na segunda versão, trocamos as linhas do ciclo de *k* e *j*:

$$
C(i, j) \text { } += A(i, k) * B(k, j)
$$

Na primeira iteração, é igual à segunda versão, mas depois, quando se altera *j* para 1, por exemplo:

$$
C(0, 1) \text { }+= A(0, 0)*B(0, 1)
$$

Esta multiplicação é feita linha a linha, aumentando em colunas e não em linhas - primeiro é (0, 0) com (0, 0), depois é (0, 0) e (0, 1) - mesma linha, coluna seguinte na segunda matriz. Ao longo do tempo é que os valores ficam completos.

Percorre-se, portanto, a matriz ao longo das suas linhas.

$$
C(0, n - 1) \text { } A(0, 0) * B(0,n - 1)
$$

Em memória os dados não estão organizados na mesma sequência em que são utilizados ou estão representados enquanto matriz - isto é importante. O sistema funciona sempre da mesma forma e vai ler os dados em segmentos. Quando é pedido um valor, um segmento é colocado em cache.

$$
t = \frac {2n^3} {Capacidade} 
$$

<aside>
❗ vTUNE - é gratuito, it seems? E dá em Windows.
</aside>

### Comandos PAPI

```jsx
papi_avail - a - ver os contadores disponíveis.
```

### Resultados PAPI

#### Alínea 1 C++

| n    | t (s)   | FLOPS         |
| ---- | ------- | ------------- |
| 600  | 0.369   | 1170731707,32 |
| 1000 | 1.846   | 1083423618,63 |
| 1400 | 6.692   | 820083682,01  |
| 1800 | 29.539  | 394867801,89  |
| 2200 | 64.955  | 327857747,67  |
| 2600 | 123.104 | 285547179,62  |
| 3000 | 208.961 | 258421427,92  |

### Resultados Tempos

#### Alínea 1 Java

| n    | t (s) | FLOPS        |
| ---- | ----- | ------------ |
| 600  | 2     | 216000000    |
| 1000 | 2     | 1000000000   |
| 1400 | 37    | 148324324,32 |
| 1800 | 119   | 98016806,7   |
| 2200 | 325   | 65526153,85  |
| 2600 | 560   | 62771428,57  |
| 3000 | 946   | 57082452,43  |

### **Alínea 2** Java

| **n** | tempo      | flops       |
| ----- | ---------- | ----------- |
| 600   | 0.1966419  | 6102.463412 |
| 1000  | 0.979317   | 2042.239643 |
| 1400  | 2.5388417  | 1102.865137 |
| 1800  | 5.21805    | 689.9128985 |
| 2200  | 9.5404427  | 461.1945314 |
| 2600  | 15.7125223 | 330.9462288 |
| 3000  | 26.5210152 | 226.2356835 |

