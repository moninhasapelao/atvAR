# Atividade Avaliativa 4 – Estruturas Avançadas de Árvores

## Parte 1 – Tipos de Árvores

### Árvore AVL

- Conceito: Árvore binária de busca (BST) autobalanceada onde a diferença de altura entre as subárvores esquerda e direita de qualquer nó é no máximo 1, criada por Adelson-Velsky e Landis em 1962. Seu principal objetivo é manter a altura da árvore próxima do ideal, garantindo operações eficientes.

- Características: Cada nó possui um fator de balanceamento, esse fator de balanceamento é a diferença entre as alturas das subárvores esquerda e direita e o valor do fator deve ser: - 1, 0, 1.

- Vantagens: Busca extremamente eficiente, altura sempre próxima de O(log n) e excelente para sistemas com muitas consultas.

- Desvantagens: Operações de inserção e remoção são lentas devido ao custo de recalcular alturas e realizar rotações frequentes. 

- Exemplo Ilustrado:

Antes do balanceamento:

```text
    30
   /
  20
 /
10
```

Após rotação simples à direita:

```text
    20
   /  \
 10   30
```

---

### Árvore Rubro-Negra
   
- Conceito: Árvore binária de busca autobalanceada que utiliza um bit extra de informação por nó para definir uma cor (vermelho ou preto).

- Regras de Coloração: Todo nó é vermelho ou preto, a raiz é sempre preta. Todas as folhas (nós nulos NIL) são pretas, se um nó é vermelho, seus filhos devem ser pretos (não há vermelhos consecutivos), o caminho de qualquer nó até suas folhas contém o mesmo número de nós pretos. 

- Vantagens: Exige menos rotações para se rebalancear após inserções/remoções se comparada à AVL. Muito utilizada em bibliotecas e sistemas operacionais.

- Desvantagens: A busca pode ser ligeiramente mais lenta que na AVL, pois a árvore é menos simétrica (a altura máxima pode chegar a \(2 \log(n+1)\)). Implementação mais complexa.

Exemplo Ilustrado:
  
          20(P)
         /     \
      10(V)   30(V)

#### (P) = Preto

#### (V) = Vermelho

---

### Árvore N-ária

- Conceito: Estrutura de dados hierárquica onde cada nó pode possuir de \(0\) até \(N\) filhos, quebrando a limitação de apenas dois ramos.

- Diferenças das Árvores Binárias: Nós contêm uma coleção dinâmica (ou vetor fixo) de ponteiros para filhos, em vez de apenas ponteiros fixos para esquerda e direita.

- Vantagens: Ideal para mapear dados com ramificações massivas, reduzindo a altura total da árvore drasticamente.

- Desvantagens: Desperdício potencial de memória com ponteiros nulos se o fator de preenchimento dos nós for baixo

- Aplicações Práticas: Organização de diretórios de sistemas de arquivos, árvores de decisão em inteligência artificial e codificação de prefixos (Árvores Trie).
Conceito


Exemplo Ilustrado: 
```text
           A
       /   |   \
      B    C    D
    / | \
   E  F  G
 ```  
---

## Operações em Árvores

### Rotação Simples à Direita (LL)

- Objetivo: Corrigir desbalanceamentos causados por excesso de nós à esquerda.

- Situação de Uso: Quando uma inserção ocorre na subárvore esquerda do filho esquerdo de um nó cujo \(FB\) ficou fora do limite (\(+2\)).

Antes:

```text
      30
     /
    20
   /
 10
```

Depois:

```text
      20
     /  \
   10   30
```

---

### Rotação Simples à Esquerda (RR)

- Objetivo: Corrigir desbalanceamentos causados por excesso de nós à direita.

- Situação Utilizada: Quando uma inserção ocorre na subárvore direita do filho direito de um nó cujo \(FB\) ficou fora do limite (\(-2\)).
Objetivo

Antes:
```text
 10
   \
   20
     \
     30
```

Depois:
```text
      20
     /  \
   10   30
```

---


### Rotação Dupla

#### Esquerda-Direita (LR) 

- Caso: Ocorre quando um nó é inserido na subárvore direita do filho esquerdo.

- Processo: Uma rotação simples à esquerda no filho, seguida por uma rotação simples à direita no pai.

Antes:
```text
      30
     /
   10
     \
     20
```   
Depois:
```text
      20
     /  \
   10   30
```
#### Primeiro: 
Rotação à esquerda em 10

#### Depois:
Rotação à direita em 30

-

#### Direita-Esquerda (RL)

- Caso: Ocorre quando um nó é inserido na subárvore esquerda do filho direito.

- Processo: Uma rotação simples à esquerda no filho, seguida por uma rotação simples à direita no pai.
Ocorre quando um nó é inserido na subárvore esquerda do filho direito.

Antes: 
```text
 10
   \
   30
   /
 20
```
Depois: 
```text
      20
     /  \
   10   30
```

#### Primeiro:
Rotação à direita em 30

#### Depois:
Rotação à esquerda em 10

---

### Inversão (Espelhamento)

- Conceito: Algoritmo que troca recursivamente os filhos esquerdo e direito de cada nó da árvore.

- Aplicação: Processamento de imagens hierárquicas, manipulação de interfaces gráficas invertidas (RTL - Right to Left) ou testes de simetria de dados. 

- Exemplo Antes e Depois

Antes:
```text
      A
     / \
    B   C
  /      \
 E        D
```
Depois:
```text
      A
     / \
    C   B
  /      \
 D        E
```
---

## Aplicação Prática

Escolha: Banco de Dados Relacional de Alto Desempenho: Estrutura de dados mais adequada para gerenciar e indexar tabelas em um banco de dados comercial de grande porte é uma variação direta da Árvore N-ária, especificamente a Árvore B+.

Justificativa Técnica: 
- Organização dos Dados e Hardware: Uma árvore binária armazena apenas uma chave por nó, exigindo que o sistema faça muitas leituras de disco sequenciais pulando de ponteiro em ponteiro. A árvore N-ária permite colocar centenas de chaves dentro de um único nó (onde \(N\) coincide perfeitamente com o tamanho do bloco do disco.
- Desempenho: Como cada nó possui múltiplos filhos, a árvore se torna extremamente "larga" e muito "baixa". Enquanto uma árvore binária com 1 milhão de registros pode ter uma altura de até 20 níveis, uma árvore N-ária balanceada (B+) precisa de apenas 3 ou 4 níveis. Isso significa encontrar qualquer registro realizando no máximo 4 acessos à memória secundária.
- Eficiência: As buscas pontuais operam em tempo garantido de (O(\log n)\). Na variação B+, as folhas da árvore N-ária são interconectadas como uma lista ligada. Isso permite que buscas por intervalos leiam os dados linearmente de forma ultra veloz assim que o primeiro elemento é localizado.

---
