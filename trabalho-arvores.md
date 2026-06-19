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

## 3. Árvore N-ária

### Conceito

Uma Árvore N-ária é uma generalização da árvore binária.

Enquanto uma árvore binária permite no máximo dois filhos por nó, uma árvore N-ária permite que cada nó possua até **N filhos**, onde N pode assumir qualquer valor inteiro maior que dois.

Essa característica permite representar hierarquias complexas de forma mais natural.

---

### Diferenças em Relação às Árvores Binárias

| Característica | Árvore Binária | Árvore N-ária |
|---------------|---------------|---------------|
| Número máximo de filhos | 2 | N |
| Estrutura | Mais simples | Mais flexível |
| Profundidade | Geralmente maior | Pode ser menor |
| Aplicação | Busca e ordenação | Hierarquias complexas |

---

### Vantagens

- Melhor representação de estruturas hierárquicas.
- Menor profundidade em alguns cenários.
- Organização mais intuitiva para categorias e subcategorias.
- Facilita modelagem de sistemas com muitos relacionamentos.

---

### Desvantagens

- Implementação mais complexa.
- Consumo de memória potencialmente maior.
- Operações de busca dependem da organização dos filhos.
- Nem sempre possui mecanismos automáticos de balanceamento.

---

### Aplicações Práticas

As árvores N-árias são amplamente utilizadas em:

- Sistemas de arquivos.
- Menus de aplicações.
- Estruturas organizacionais empresariais.
- Árvores DOM de páginas web.
- Classificações biológicas.
- Sistemas de categorias em e-commerces.

---

### Exemplo ilustrado
<img width="406" height="246" alt="image" src="https://github.com/user-attachments/assets/f4f0b1d9-9ce1-407c-bb67-fba40de47645" />

  
---

# Parte 2 – Operações em Árvores

## 1. Rotação Simples à Direita

### Objetivo

A rotação simples à direita é utilizada para corrigir desequilíbrios causados pelo crescimento excessivo da subárvore esquerda.

O objetivo é redistribuir os nós para reduzir a altura desse lado da árvore.

---

### Situação em que é Utilizada

É aplicada quando ocorre um desequilíbrio do tipo:

**Esquerda-Esquerda (LL)**

Isso significa que um novo elemento foi inserido no filho esquerdo do filho esquerdo do nó desbalanceado.

---

### Funcionamento

O filho esquerdo assume a posição do nó desbalanceado.

O antigo nó torna-se filho direito desse novo nó.

Essa reorganização reduz a altura da árvore e restaura o balanceamento.

---

### Exemplo

<img width="392" height="244" alt="image" src="https://github.com/user-attachments/assets/4a21afb0-792d-4a51-870f-e0148ba6e843" />


---

## 2. Rotação Simples à Esquerda

### Objetivo

Corrigir desequilíbrios provocados pelo crescimento excessivo da subárvore direita.

---

### Situação em que é Utilizada

É aplicada quando ocorre um desequilíbrio do tipo:

**Direita-Direita (RR)**

Nesse caso, a inserção ocorreu no filho direito do filho direito do nó desbalanceado.

---

### Funcionamento

O filho direito assume a posição do nó desbalanceado.

O antigo nó passa a ocupar a posição de filho esquerdo.

Com isso, a árvore volta a ficar equilibrada.

---

### Exemplo

<img width="368" height="242" alt="image" src="https://github.com/user-attachments/assets/d6c8bb78-7228-4487-8942-cd3ee01df992" />

---

## 3. Árvore N-ária

### Conceito

Uma Árvore N-ária é uma generalização da árvore binária.

Enquanto uma árvore binária permite no máximo dois filhos por nó, uma árvore N-ária permite que cada nó possua até **N filhos**, onde N pode assumir qualquer valor inteiro maior que dois.

Essa característica permite representar hierarquias complexas de forma mais natural.

---

### Diferenças em Relação às Árvores Binárias

| Característica | Árvore Binária | Árvore N-ária |
|---------------|---------------|---------------|
| Número máximo de filhos | 2 | N |
| Estrutura | Mais simples | Mais flexível |
| Profundidade | Geralmente maior | Pode ser menor |
| Aplicação | Busca e ordenação | Hierarquias complexas |

---

### Vantagens

- Melhor representação de estruturas hierárquicas.
- Menor profundidade em alguns cenários.
- Organização mais intuitiva para categorias e subcategorias.
- Facilita modelagem de sistemas com muitos relacionamentos.

---

### Desvantagens

- Implementação mais complexa.
- Consumo de memória potencialmente maior.
- Operações de busca dependem da organização dos filhos.
- Nem sempre possui mecanismos automáticos de balanceamento.

---

### Aplicações Práticas

As árvores N-árias são amplamente utilizadas em:

- Sistemas de arquivos.
- Menus de aplicações.
- Estruturas organizacionais empresariais.
- Árvores DOM de páginas web.
- Classificações biológicas.
- Sistemas de categorias em e-commerces.

---

### Exemplo ilustrado
<img width="406" height="246" alt="image" src="https://github.com/user-attachments/assets/f4f0b1d9-9ce1-407c-bb67-fba40de47645" />

  
---

# Parte 2 – Operações em Árvores

## 1. Rotação Simples à Direita

### Objetivo

A rotação simples à direita é utilizada para corrigir desequilíbrios causados pelo crescimento excessivo da subárvore esquerda.

O objetivo é redistribuir os nós para reduzir a altura desse lado da árvore.

---

### Situação em que é Utilizada

É aplicada quando ocorre um desequilíbrio do tipo:

**Esquerda-Esquerda (LL)**

Isso significa que um novo elemento foi inserido no filho esquerdo do filho esquerdo do nó desbalanceado.

---

### Funcionamento

O filho esquerdo assume a posição do nó desbalanceado.

O antigo nó torna-se filho direito desse novo nó.

Essa reorganização reduz a altura da árvore e restaura o balanceamento.

---

### Exemplo

<img width="392" height="244" alt="image" src="https://github.com/user-attachments/assets/4a21afb0-792d-4a51-870f-e0148ba6e843" />


---

## 2. Rotação Simples à Esquerda

### Objetivo

Corrigir desequilíbrios provocados pelo crescimento excessivo da subárvore direita.

---

### Situação em que é Utilizada

É aplicada quando ocorre um desequilíbrio do tipo:

**Direita-Direita (RR)**

Nesse caso, a inserção ocorreu no filho direito do filho direito do nó desbalanceado.

---

### Funcionamento

O filho direito assume a posição do nó desbalanceado.

O antigo nó passa a ocupar a posição de filho esquerdo.

Com isso, a árvore volta a ficar equilibrada.

---

### Exemplo

<img width="368" height="242" alt="image" src="https://github.com/user-attachments/assets/d6c8bb78-7228-4487-8942-cd3ee01df992" />

---

## 3. Rotação Dupla

Em algumas situações, uma única rotação não é suficiente para restaurar o balanceamento.

Nesses casos, utiliza-se uma rotação dupla.

---

### Rotação Esquerda-Direita (LR)

#### Quando ocorre

Quando o desequilíbrio está à esquerda, mas o novo elemento foi inserido na subárvore direita do filho esquerdo.

#### Procedimento

1. Realiza-se uma rotação simples à esquerda no filho esquerdo.
2. Em seguida, realiza-se uma rotação simples à direita no nó desbalanceado.

---

### Rotação Direita-Esquerda (RL)

#### Quando ocorre

Quando o desequilíbrio está à direita, mas o novo elemento foi inserido na subárvore esquerda do filho direito.

#### Procedimento

1. Realiza-se uma rotação simples à direita no filho direito.
2. Em seguida, realiza-se uma rotação simples à esquerda no nó desbalanceado.

---

### Importância das Rotações Duplas

As rotações duplas são essenciais para garantir que a árvore permaneça balanceada mesmo em situações mais complexas de inserção e remoção.

Sem elas, alguns desequilíbrios não poderiam ser corrigidos adequadamente.

---

### Exemplo

<img width="462" height="213" alt="image" src="https://github.com/user-attachments/assets/0f47dad9-61d7-412c-b79b-dc56fe188d93" />

---

## 4. Inversão (Espelhamento)

### Conceito

A inversão, também chamada de espelhamento, é uma operação que troca recursivamente os filhos esquerdo e direito de todos os nós da árvore.

O resultado é uma nova árvore que representa o reflexo da estrutura original.

---

### Aplicações

- Testes de algoritmos.
- Estudos acadêmicos.
- Processamento de estruturas hierárquicas.
- Transformações gráficas.
- Verificação de propriedades de árvores.

---

### Resultado da Operação

Após a execução do espelhamento:

- Todos os filhos esquerdos tornam-se direitos.
- Todos os filhos direitos tornam-se esquerdos.
- A hierarquia permanece a mesma.
- Apenas a orientação da árvore é alterada.

---

### Exemplo

<img width="306" height="212" alt="image" src="https://github.com/user-attachments/assets/5dfe0053-fc26-4aec-8862-3c9d1c98a09a" />

---

# Parte 3 – Aplicação Prática

## Sistema de Busca de Dados

Uma aplicação que realiza grande quantidade de consultas em memória, como mecanismos de busca internos ou sistemas de indexação, pode utilizar uma Árvore AVL.

### Justificativa

O principal requisito desses sistemas é a velocidade de pesquisa.

Como a Árvore AVL mantém um balanceamento rigoroso, sua altura permanece próxima de `log(n)` mesmo após milhares de inserções.

Isso garante:

- Tempo de busca extremamente eficiente.
- Menor quantidade de comparações.
- Respostas rápidas ao usuário.
- Desempenho consistente independentemente da ordem de inserção dos dados.

Embora as inserções e remoções sejam mais custosas devido às rotações necessárias, o benefício obtido durante as buscas compensa esse custo em aplicações onde as consultas são mais frequentes do que as atualizações.

Por esse motivo, a Árvore AVL é considerada uma excelente escolha para sistemas de busca.

---

# Parte 4 – Comparação entre Estruturas

| Estrutura | Nº Máximo de Filhos | Balanceamento | Complexidade de Busca | Complexidade de Inserção | Vantagem Principal | Desvantagem Principal | Exemplo de Aplicação |
|------------|-------------------|---------------|----------------------|-------------------------|-------------------|----------------------|---------------------|
| BST | 2 | Não possui balanceamento automático. Pode tornar-se desbalanceada dependendo da ordem de inserção dos elementos. | O(log n) no melhor caso e O(n) no pior caso. | O(log n) no melhor caso e O(n) no pior caso. | Simplicidade de implementação. | Perda significativa de desempenho quando desbalanceada. | Estruturas básicas de busca e ensino de algoritmos. |
| AVL | 2 | Sim. Utiliza fator de balanceamento e rotações automáticas para manter equilíbrio rigoroso. | O(log n). | O(log n). | Busca extremamente eficiente e previsível. | Inserções e remoções mais complexas devido ao balanceamento constante. | Sistemas de busca e indexação. |
| Rubro-Negra | 2 | Sim. Utiliza regras de coloração e rotações para manter balanceamento aproximado. | O(log n). | O(log n). | Menor quantidade de rotações durante atualizações. | Implementação mais complexa devido às regras de coloração. | Bibliotecas padrão, kernels e estruturas internas de sistemas. |
| N-ária | N | Pode possuir ou não mecanismos de balanceamento, dependendo da implementação utilizada. | O(log n) em versões balanceadas ou variável conforme a aplicação. | O(log n) ou variável conforme a implementação. | Excelente representação de hierarquias complexas. | Estrutura mais complexa e dependente da aplicação. | Sistemas de arquivos, menus e taxonomias. |


## Análise Explicativa das Estruturas

A comparação entre as estruturas mostra como diferentes estratégias de organização e balanceamento influenciam diretamente o desempenho das operações realizadas sobre os dados.

A BST é a estrutura mais simples entre as analisadas. Sua principal vantagem está na facilidade de implementação e no baixo custo de manutenção. Entretanto, por não possuir mecanismos automáticos de balanceamento, seu desempenho pode se deteriorar significativamente quando os dados são inseridos em uma ordem desfavorável. Nesses casos, a árvore pode assumir um formato semelhante a uma lista encadeada, tornando as operações menos eficientes.

A Árvore AVL foi desenvolvida justamente para resolver esse problema. Seu balanceamento rigoroso garante que a altura da árvore permaneça controlada, proporcionando tempos de busca muito consistentes. Essa característica torna a AVL especialmente adequada para aplicações nas quais as consultas são realizadas com frequência muito maior do que as inserções e remoções. O custo adicional necessário para manter o balanceamento é compensado pelo ganho de desempenho durante as pesquisas.

A Árvore Rubro-Negra adota uma abordagem diferente. Em vez de manter um equilíbrio rigoroso como a AVL, ela aceita pequenos desequilíbrios controlados. Essa estratégia reduz a quantidade de rotações necessárias durante inserções e remoções, tornando essas operações mais eficientes. Por esse motivo, árvores Rubro-Negras são amplamente utilizadas em implementações de bibliotecas padrão e componentes internos de sistemas operacionais, onde há necessidade de equilíbrio entre desempenho de busca e custo de atualização.

Já a Árvore N-ária não foi criada com foco principal em busca eficiente, mas sim na representação de hierarquias complexas. Sua capacidade de armazenar vários filhos em um mesmo nó permite modelar estruturas organizacionais, sistemas de arquivos e menus de navegação de forma mais natural. Dependendo da implementação, ela pode apresentar diferentes níveis de eficiência, sendo mais indicada para organização hierárquica do que para buscas intensivas.

De maneira geral, observa-se que não existe uma estrutura universalmente melhor. A escolha depende das necessidades da aplicação. Quando a prioridade é simplicidade, a BST pode ser suficiente. Quando o objetivo é maximizar o desempenho das buscas, a AVL costuma ser a melhor opção. Para sistemas com muitas inserções e remoções, a Rubro-Negra oferece um equilíbrio mais adequado. Já para representar relações hierárquicas complexas, as árvores N-árias apresentam vantagens significativas.

---

# Conclusão

As estruturas avançadas de árvores foram desenvolvidas para superar as limitações das Árvores Binárias de Busca tradicionais. As Árvores AVL oferecem excelente desempenho em buscas por meio de um balanceamento rigoroso. As Árvores Rubro-Negras apresentam um equilíbrio entre desempenho e custo de manutenção, sendo amplamente utilizadas em sistemas reais. Já as Árvores N-árias permitem representar hierarquias complexas de maneira eficiente e intuitiva.

A escolha da estrutura ideal depende diretamente das necessidades da aplicação, do volume de dados armazenados e da frequência das operações de busca, inserção e remoção realizadas pelo sistema.
