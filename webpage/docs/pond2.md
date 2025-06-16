---
sidebar_position: 12
slug: /pond2
title: Classificador de imagens
---

Este projeto tem por objetivo construir um visualizador de imagens que permita a aplicação de um classificador customizado treinado pelo desenvolvedor. As imagens devem ser exibidas da webcam do usuário ou de um arquivo local, e o classificador deve ser capaz de identificar e classificar as imagens em diferentes categorias.

As categorias que o classificador deve ser capaz de identificar podem incluir, mas não estão limitadas a:
- Animais (cachorros, gatos, pássaros, etc.)
- Objetos (carros, bicicletas, etc.)
- Cenários (praias, montanhas, florestas, etc.)
- Pessoas (adultos, crianças, idosos, etc.)
- Alimentos (frutas, vegetais, pratos prontos, etc.)

O classificador deve ser capaz de lidar com diferentes condições de iluminação e ângulos de visão, e deve ser treinado com um conjunto de dados representativo das categorias mencionadas.

O visualizador deve permitir ao usuário escolher entre usar a webcam ou carregar uma imagem de um arquivo local. O classificador deve ser capaz de processar a imagem e exibir o resultado da classificação na tela, juntamente com a imagem original.

Não é necessário capturar e exibir o vídeo da webcam em tempo real, mas o classificador deve ser capaz de processar imagens estáticas capturadas pela webcam.

O algoritmos classificador pode ser implementado utilizando bibliotecas como o Skit-learn, focar nos algoritmos de visão computacional clássicos, como SVM, Decision Trees, Random Forests, entre outros. O classificador deve ser capaz de lidar com diferentes tamanhos de imagem e deve ser otimizado para garantir um desempenho adequado.

Apresentar no README do projeto uma breve descrição do classificador, incluindo o algoritmo utilizado, as categorias de imagens que ele é capaz de identificar e o conjunto de dados utilizado para o treinamento. Incluir também instruções sobre como executar o projeto e como utilizar o visualizador. Trazer também os dados do desempenho do classificador, como acurácia, precisão e recall, para que o usuário possa entender a eficácia do classificador.

**Requisitos:**

    - O visualizador deve ser implementado em Python, utilizando alguma biblioteca de interface gráfica local, como o [FreeSimpleGUI](https://freesimplegui.readthedocs.io/en/latest/), para a interface gráfica.
    - O carregamento da imagem deve ser feito através de um diálogo de arquivo, permitindo ao usuário escolher a imagem desejada.
    - Também deve ser possível capturar imagens da webcam do usuário.
    - O classificador deve ser capaz de identificar e classificar as imagens em diferentes categorias.

**Padrão de Qualidade:**

    - O código deve estar estruturado de forma clara, legível, modular e construído de acordo com as boas práticas de programação.
    - O visualizador deve ter uma interface amigável e intuitiva, com botões e menus claros para a exibição do resultado do classificador.
    - O visualizador deve ser testado com diferentes imagens para garantir que o classificador funciona corretamente.
    - Todo o projeto deve ser entregue em um repositório do GitHub, com um README claro e conciso, explicando como executar o projeto e suas funcionalidades.


---

## Alternativa

Para quem ainda não implementou a atividade ponderada acima, você podem fazer essa implementação de exercício:

**Exercício: Implementação de uma Calculadora em Notação Polonesa Reversa (RPN)**

---

### 1. Contexto

A **Notação Polonesa Reversa** (RPN – *Reverse Polish Notation*), também chamada de **postfix**, é uma forma de representar expressões matemáticas em que o operador vem **após** seus operandos. Por exemplo, a expressão infixa

```
(3 + 4) × 5
```

em RPN fica:

```
3 4 + 5 ×
```

Esse formato elimina a necessidade de parênteses e facilita a avaliação de expressões usando uma **pilha**:

1. Ao ler um número, empilha-o.
2. Ao ler um operador, desempilha os dois últimos números, aplica a operação e empilha o resultado.

Calculadoras da HP e muitas linguagens de script usam RPN por sua eficiência.

:::tip[Notação Polonesa Reversa]

<iframe width="560" height="315" src="https://www.youtube.com/embed/7ha78yWRDlE?si=fGqZyMKWrRs4hu6M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style={{marginLeft:'auto', marginRight:'auto', display:'block', width:'60%'}}></iframe>
<br />

:::

---

### 2. Objetivo

Desenvolver, em linguagem C (ou pseudocódigo), uma **calculadora** que:

1. **Leia** uma expressão em RPN (como uma sequência de tokens separados por espaço).
2. **Utilize** uma implementação de **pilha** para armazenar operandos.
3. **Avalie** a expressão e **imprima** o resultado numérico.

---

### 3. Descrição da Atividade

1. **Implementar o TAD Pilha**

   * Operações mínimas:

     * `inicializaPilha()`
     * `push(pilha, valor)`
     * `valor = pop(pilha)`
     * `estaVazia(pilha)`

2. **Leitura e Tokenização**

   * Leia uma linha de texto representando a expressão RPN (por exemplo: `"5 1 2 + 4 * + 3 –"`).
   * Separe-a em tokens (números ou operadores).

3. **Avaliação da Expressão**

   * Para cada token:

     * Se for número: `push(pilha, número)`.
     * Se for operador (`+`, `-`, `*`, `/`):

       1. `b = pop(pilha)`
       2. `a = pop(pilha)`
       3. `res = a operador b`
       4. `push(pilha, res)`

4. **Resultado Final**

   * Ao final da leitura, o topo da pilha deve conter o resultado da expressão.
   * Imprima-o na saída padrão.

---

### 4. Requisitos Mínimos

* Suporte a operações básicas:

  * **Adição** (`+`), **Subtração** (`-`), **Multiplicação** (`*`), **Divisão** (`/`).
* Tratamento de **expressões bem formadas**; não é necessário lidar com erros de sintaxe (mas pode ser considerado um **desafio extra**).
* Utilizar exclusivamente o TAD Pilha para manipulação de operandos.

---

### 5. Exemplos de Uso

| Expressão RPN       | Avaliação passo a passo                                                                                     | Resultado |
| ------------------- | ----------------------------------------------------------------------------------------------------------- | --------- |
| `3 4 +`             | push 3; push 4; pop b=4, a=3; push (3+4)=7                                                                  | 7         |
| `5 1 2 + 4 * + 3 -` | …  → push(5); push(1); push(2); → pop2,1→3; push3; push4; pop4,3→12; push12; pop12,5→17; push17; pop3,17→14 | 14        |

---

### 6. Critérios de Avaliação

1. **Correta implementação** das operações de pilha.
2. **Leitura e tokenização** eficiente da expressão.
3. **Avaliação correta** de várias expressões RPN.
4. **Clareza do código**: uso de funções, comentários e tratamento de casos especiais (desafios).

---

Entregar o link para o repositório com a solução. No **readme**, explicar como foi realizada a implementação do algoritmo.



