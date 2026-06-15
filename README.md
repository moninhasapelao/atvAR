# Atividade Avaliativa 4 – Estruturas Avançadas de Árvores

## Parte 1 – Tipos de Árvores

### Árvore AVL

- Conceito: Árvore binária de busca (BST) autobalanceada onde a diferença de altura entre as subárvores esquerda e direita de qualquer nó é no máximo 1, criada por Adelson-Velsky e Landis em 1962. Seu principal objetivo é manter a altura da árvore próxima do ideal, garantindo operações eficientes.

- Características: Cada nó possui um fator de balanceamento, esse fator de balanceamento é a diferença entre as alturas das subárvores esquerda e direita e o valor do fator deve ser: - 1, 0, 1.

- Vantagens: Busca extremamente eficiente, altura sempre próxima de O(log n) e excelente para sistemas com muitas consultas.

- Desvantagens: Operações de inserção e remoção são lentas devido ao custo de recalcular alturas e realizar rotações frequentes. 

- Exemplo Ilustrado:

Antes do balanceamento:

      30
     /
    20
   /
   10
   
Após rotação simples à direita:

      20
     /  \
   10   30
 
---

### Árvore Rubro-Negra
   
- Conceito: Árvore binária de busca autobalanceada que utiliza um bit extra de informação por nó para definir uma cor (vermelho ou preto).

- Regras de Coloração: Todo nó é vermelho ou preto. A raiz é sempre preta. Todas as folhas (nós nulos NIL) são pretas. Se um nó é vermelho, seus filhos devem ser pretos (não há vermelhos consecutivos). O caminho de qualquer nó até suas folhas contém o mesmo número de nós pretos. 

- Vantagens: Exige menos rotações para se rebalancear após inserções/remoções se comparada à AVL. Muito utilizada em bibliotecas e sistemas operacionais.

- Desvantagens: A busca pode ser ligeiramente mais lenta que na AVL, pois a árvore é menos simétrica (a altura máxima pode chegar a \(2 \log(n+1)\)). Implementação mais complexa.

- Exemplo Ilustrado:
  
          20(P)
         /     \
      10(V)   30(V)

#### (P) = Preto

#### (V) = Vermelho

---

## Árvore N-ária

- Conceito: Estrutura de dados hierárquica onde cada nó pode possuir de \(0\) até \(N\) filhos, quebrando a limitação de apenas dois ramos.

- Diferenças das Árvores Binárias: Nós contêm uma coleção dinâmica (ou vetor fixo) de ponteiros para filhos, em vez de apenas ponteiros fixos para esquerda e direita.

- Vantagens: Ideal para mapear dados com ramificações massivas, reduzindo a altura total da árvore drasticamente.

- Desvantagens: Desperdício potencial de memória com ponteiros nulos se o fator de preenchimento dos nós for baixo

- Aplicações Práticas: Organização de diretórios de sistemas de arquivos, árvores de decisão em inteligência artificial e codificação de prefixos (Árvores Trie).
Conceito


Exemplo Ilustrado: 

           A
       /   |   \
      B    C    D
    / | \
   E  F  G
   
---

## Operações em Árvores

### Rotação Simples à Direita

- Objetivo: Corrigir desbalanceamentos causados por excesso de nós à esquerda.

- Situação de Uso: Quando uma inserção ocorre na subárvore esquerda do filho esquerdo de um nó cujo \(FB\) ficou fora do limite (\(+2\)).

- Antes:
      30
     /
    20
   /
 10
  
- Depois:
      20
     /  \
   10   30

---

2. Rotação Simples à Esquerda
Objetivo

Corrigir desbalanceamentos causados por excesso de nós à direita.

Situação de Uso

Caso Direita-Direita (RR).

Antes
 10
   \
   20
     \
     30
Depois
      20
     /  \
   10   30
3. Rotação Dupla
Esquerda-Direita (LR)

Ocorre quando um nó é inserido na subárvore direita do filho esquerdo.

Antes
      30
     /
   10
     \
     20
Depois
      20
     /  \
   10   30

Primeiro:

Rotação à esquerda em 10

Depois:

Rotação à direita em 30
Direita-Esquerda (RL)

Ocorre quando um nó é inserido na subárvore esquerda do filho direito.

Antes
 10
   \
   30
   /
 20
Depois
      20
     /  \
   10   30

Primeiro:

Rotação à direita em 30

Depois:

Rotação à esquerda em 10
4. Inversão (Espelhamento)
Conceito

Consiste em trocar recursivamente todos os filhos esquerdos pelos direitos.

Aplicação
Processamento de imagens.
Algoritmos de árvores.
Testes e validações de estruturas.
Antes
      A
     / \
    B   C
Depois
      A
     / \
    C   B
Parte 3 – Aplicação Prática
Sistema de Banco de Dados

A estrutura mais adequada é a Árvore Rubro-Negra.

Justificativa

Bancos de dados realizam constantemente:

Inserções
Remoções
Atualizações
Buscas

A árvore Rubro-Negra oferece:

Busca em O(log n)
Inserção em O(log n)
Remoção em O(log n)
Menor quantidade de rotações em comparação com AVL

Por esse motivo, diversas bibliotecas de estruturas de dados utilizam árvores Rubro-Negras internamente.

Exemplo

Um índice de clientes poderia armazenar:

Cliente ID
|
├── 1001
├── 1002
├── 1003
└── ...

A árvore mantém os registros organizados para acesso rápido.
