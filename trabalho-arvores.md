# Atividade Avaliativa 4 – Estruturas Avançadas de Árvores

## Introdução

As Árvores Binárias de Busca (BST – Binary Search Trees) são estruturas de dados amplamente utilizadas para armazenar e organizar informações de forma hierárquica. Entretanto, dependendo da ordem em que os elementos são inseridos, uma BST pode se tornar desbalanceada, reduzindo significativamente seu desempenho.

Para resolver esse problema, foram desenvolvidas estruturas avançadas de árvores capazes de manter um balanceamento adequado, garantindo operações eficientes de busca, inserção e remoção. Entre as principais estruturas estão as Árvores AVL, Árvores Rubro-Negras e Árvores N-árias.

Este trabalho apresenta as características dessas estruturas, as principais operações de balanceamento e uma análise de suas aplicações práticas na computação.

---

# Parte 1 – Tipos de Árvores

## 1. Árvore AVL

### Conceito

A Árvore AVL é uma árvore binária de busca auto balanceada criada pelos cientistas soviéticos Georgy Adelson-Velsky e Evgenii Landis em 1962. Seu principal objetivo é evitar que a árvore se torne muito profunda em um dos lados, garantindo que a altura permaneça próxima do ideal.

Para isso, a AVL monitora constantemente o chamado **Fator de Balanceamento (FB)**, que corresponde à diferença entre a altura da subárvore esquerda e da subárvore direita de um nó.

A árvore é considerada balanceada quando o fator de balanceamento de todos os nós está entre **-1 e +1**.

Caso algum nó ultrapasse esse limite, a estrutura realiza rotações automáticas para restaurar o equilíbrio.

---

### Características

- É uma árvore binária de busca.
- Cada nó possui no máximo dois filhos.
- Mantém controle rigoroso do balanceamento.
- Utiliza rotações simples e duplas para corrigir desequilíbrios.
- Garante que a altura da árvore permaneça próxima de `log(n)`.
- Oferece excelente desempenho para operações de busca.

---

### Vantagens

- Busca extremamente rápida e previsível.
- Mantém a árvore sempre próxima do formato ideal.
- Reduz a quantidade de comparações necessárias durante pesquisas.
- Excelente para sistemas que realizam muitas consultas.

---

### Desvantagens

- Inserções e remoções exigem verificações constantes do balanceamento.
- Pode realizar várias rotações durante atualizações.
- Implementação mais complexa que uma BST tradicional.
- Consome mais recursos para manter o controle da altura dos nós.

---

### Exemplo ilustrado
<img width="407" height="258" alt="image" src="https://github.com/user-attachments/assets/82fac8fb-62d5-48a2-9856-491fdde8d1fa" />


---

## 2. Árvore Rubro-Negra

### Conceito

A Árvore Rubro-Negra é uma árvore binária de busca auto balanceada que utiliza um sistema de cores para controlar sua estrutura.

Cada nó recebe uma das duas cores possíveis:

- Vermelho
- Preto

Essas cores não possuem significado visual apenas; elas servem para garantir propriedades matemáticas que mantêm a árvore aproximadamente balanceada.

Diferentemente da AVL, que busca um balanceamento rigoroso, a Rubro-Negra permite pequenos desequilíbrios, reduzindo a quantidade de rotações necessárias.

Essa característica torna a estrutura muito utilizada em bibliotecas padrão de linguagens de programação e sistemas operacionais.

---

### Regras de Coloração

Para manter o balanceamento, toda árvore Rubro-Negra deve obedecer às seguintes regras:

1. Todo nó é vermelho ou preto.
2. A raiz sempre deve ser preta.
3. Todas as folhas nulas são consideradas pretas.
4. Um nó vermelho não pode possuir um filho vermelho.
5. Todo caminho da raiz até uma folha nula deve possuir a mesma quantidade de nós pretos.

Essas regras impedem que a árvore fique excessivamente inclinada para um dos lados.

---

### Vantagens

- Balanceamento eficiente com menor custo de manutenção.
- Menor número de rotações em comparação com AVL.
- Inserções e remoções geralmente mais rápidas.
- Amplamente utilizada em aplicações reais.

---

### Desvantagens

- Estrutura mais difícil de implementar.
- Regras de coloração aumentam a complexidade do algoritmo.
- Busca ligeiramente menos eficiente que AVL devido ao balanceamento menos rigoroso.

---

### Exemplo ilustrado
  <img width="377" height="243" alt="image" src="https://github.com/user-attachments/assets/11cae79e-4620-493e-be26-9bedaaf10a97" />


---
