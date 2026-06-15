Atividade Avaliativa 4 – Estruturas Avançadas de Árvores

Parte 1 – Tipos de Árvores

1. Árvore AVL 
Conceito

A árvore AVL é uma Árvore Binária de Busca (BST) autobalanceada criada por Adelson-Velsky e Landis em 1962. Seu principal objetivo é manter a altura da árvore próxima do ideal, garantindo operações eficientes.

Características: Cada nó possui um fator de balanceamento ; O fator de balanceamento é a diferença entre as alturas das subárvores esquerda e direita; O valor do fator deve ser:

-1
0
1
Quando o balanceamento é violado, são realizadas rotações.

Vantagens

Busca extremamente eficiente. 
Altura sempre próxima de O(log n).
Excelente para sistemas com muitas consultas.

Desvantagens

Inserções e remoções mais complexas.
Necessita realizar rotações para manter o equilíbrio.
Exemplo Ilustrado

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

2. Árvore Rubro-Negra
   
Conceito

A árvore Rubro-Negra é uma BST balanceada que utiliza cores para controlar o crescimento da árvore.

Cada nó recebe uma das duas cores:

Vermelho
Preto

O balanceamento é mantido através de regras de coloração e rotações.

Regras de Coloração
Todo nó é vermelho ou preto.
A raiz sempre é preta.
Nós nulos são considerados pretos.
Um nó vermelho não pode ter filho vermelho.
Todos os caminhos da raiz até uma folha possuem a mesma quantidade de nós pretos.
Vantagens
Menos rotações que AVL.
Inserção e remoção mais rápidas.
Muito utilizada em bibliotecas e sistemas operacionais.
Desvantagens
Implementação mais complexa.
Busca ligeiramente menos eficiente que AVL.
Exemplo Ilustrado
          20(P)
         /     \
      10(V)   30(V)

(P) = Preto

(V) = Vermelho

3. Árvore N-ária
Conceito

É uma árvore em que cada nó pode possuir até N filhos.

Diferente das árvores binárias, não existe limitação de apenas dois filhos.

Diferenças em Relação às Árvores Binárias
Árvore Binária	Árvore N-ária
Máximo 2 filhos	Máximo N filhos
Estrutura simples	Estrutura mais flexível
Muito usada em busca	Muito usada em hierarquias
Vantagens
Representa hierarquias naturalmente.
Menor profundidade quando há muitos elementos.
Facilita modelagem de estruturas reais.
Desvantagens
Implementação mais complexa.
Operações podem exigir mais memória.
Exemplo Ilustrado
           A
       /   |   \
      B    C    D
    / | \
   E  F  G
Aplicações Práticas
Sistemas de arquivos
Menus de aplicativos
Organogramas empresariais
XML e HTML
Taxonomias biológicas
Parte 2 – Operações em Árvores
1. Rotação Simples à Direita
Objetivo

Corrigir desbalanceamentos causados por excesso de nós à esquerda.

Situação de Uso

Caso Esquerda-Esquerda (LL).

Antes
      30
     /
    20
   /
 10
Depois
      20
     /  \
   10   30
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
