---
sidebar_position: 1
slug: /perceptron
title: O perceptron
---

# O Perceptron

## 1. Contexto histórico

O **perceptron** foi proposto por **Frank Rosenblatt** em 1957, no Cornell Aeronautical Laboratory, como uma concretização prática do neurônio lógico descrito por McCulloch & Pitts em 1943. A ideia era criar uma “máquina que aprende” inspirada nos neurônios biológicos e capaz de reconhecer padrões sem programação explícita.

Na época, computadores digitais eram raros, caros e lentos. O **Mark I Perceptron** (1960) — implementação física de Rosenblatt com 512 fotorresistores e pequenos motores que ajustavam os pesos — ilustra essas limitações: pouquíssima memória, quase nada de ponto‑flutuante e muitos componentes analógicos.

Um neurônio biológico típico recebe sinais elétricos em milhares de dendritos, integra essas correntes no corpo celular e, caso o valor resultante supere um limiar, dispara um potencial de ação que percorre o axônio até as terminações sinápticas, liberando neurotransmissores. Esse ciclo de integração‑e‑disparo motivou Rosenblatt a representar:

* dendritos → **entradas** `x_i`
* sinapses → **pesos** ajustáveis `w_i`
* limiar → **bias** `b`
* disparo → **função de ativação**

Assim, o perceptron traduz o comportamento eletroquímico do neurônio em operações algébricas simples, executáveis em hardware ou software.

Três princípios desse modelo são:

1. **Sinapses têm pesos.** Cada conexão possui força ajustável (`w_i`).
2. **Potenciais se somam.** O neurônio soma sinais de entrada; o perceptron calcula `z = Σ w_i x_i + b`.
3. **Disparo tudo‑ou‑nada.** O neurônio só dispara se o potencial ultrapassar um limiar; no perceptron isso vira uma função de ativação.

## 2. Perceptron com dois inputs

### 2.1. Exemplo

Queremos decidir **aprovar ou não** um microcrédito usando duas variáveis normalizadas (entre 0 e 1):

* `x1`: score de crédito
* `x2`: renda mensal (em kR\$)

Pesos fictícios (incluindo o bias `w0`):

| Peso        | Valor |
| ----------- | ----- |
| `w0` (bias) | −0.6  |
| `w1`        | 0.8   |
| `w2`        | 0.7   |

Para um candidato com `x1 = 0.9` e `x2 = 0.6`:

```
z = w0 + w1 * x1 + w2 * x2
  = -0.6 + 0.8*0.9 + 0.7*0.6
  = 0.54
```

Sem função de ativação, interpretamos `z` como score: se for positivo, aprovamos o empréstimo (0.54 > 0).

:::tip Exercício

Implemente um script que receba `x1` e `x2`, calcule `z` com os pesos acima e imprima o valor e a decisão **Aprovado** ou **Negado**.

:::

### 2.2. A função de ativação

Para converter o score contínuo em decisão discreta, aplicamos uma **função de ativação**. No exemplo usaremos o **degrau de Heaviside**:

```
step(z) = 1  se z >= 0
           0  caso contrário
```

Como `z = 0.54`, `step(0.54) = 1` → **aprovado**.

:::tip Exercício

Crie a função `step(z)` conforme acima e integre‑a ao exercício anterior.

:::

### 2.3. O algoritmo de aprendizado

Algoritmo Perceptron (pseudocódigo):

1. Inicialize pesos (`w0`, `w1`, `w2`) com valores pequenos aleatórios e escolha a taxa de aprendizado `eta`.
2. Para cada época:

   * Para cada amostra (`x1`, `x2`, `y`):

     1. `z = w0 + w1*x1 + w2*x2`
     2. `y_hat = step(z)`
     3. `erro = y - y_hat`
     4. Atualize:
        * `w1 += eta * erro * x1`
        * `w2 += eta * erro * x2`
        * `w0 += eta * erro`  (bias)
3. Pare quando não houver erros ou após `max_epochs`.

:::tip Exercício

Treine um perceptron de duas entradas para reproduzir as portas lógicas **OR**, **NAND** e **AND**. Teste todas as combinações.

:::

### 2.4. O papel do bias

O **bias** desloca a fronteira de decisão. Sem ele, a reta `w1*x1 + w2*x2 = 0` passa obrigatoriamente pela origem; com o termo `w0`, podemos movê‑la para classificar conjuntos que não são simétricos em torno da origem.

:::tip Exercício

Repita o exercício das portas lógicas fixando `w0 = 0`. Quais portas ainda podem ser aprendidas? Explique.

:::

### 2.5. A limitação do perceptron

Um único perceptron só resolve **problemas linearmente separáveis**. A porta **XOR** exige uma fronteira não‑linear e, portanto, é inalcançável para um perceptron isolado. Essa limitação, apontada por Minsky & Papert (1969), esfriou a pesquisa até o surgimento das redes multicamadas e do algoritmo de retropropagação na década de 1980.

:::tip Exercício

Tente treinar um perceptron de duas entradas para aprender **XOR** e observe por que o erro nunca zera.

:::

:::tip Exercício

Utilizando um perceptron treinado para representar uma porte and, outro para
uma porta nand e outro para uma porta or, crie um conjunto de perceptrons que
representem a porta XOR.

:::
