# exercício 1 - Classificação de pedido

 ### 1.1 — Blocos básicos

 - **N1:** Início + `desconto = 0`
- **N2:** Decisão `valor >= 500`
- **N3:** `desconto = 10`
- **N4:** Decisão `clienteVip`
- **N5:** `desconto += 5`
- **N6:** Decisão `!pagamentoAprovado`
- **N7:** `return "PAGAMENTO RECUSADO"`
- **N8:** Cálculo de `valorFinal`
- **N9:** `return "PEDIDO APROVADO: " + valorFinal`

 ### 1.2 — Decisões

 Existem **3 decisões**:

 - **D1:** `valor >= 500`
- **D2:** `clienteVip`
- **D3:** `!pagamentoAprovado`

 Cada decisão possui dois caminhos:

 - **V:** condição verdadeira
- **F:** condição falsa

 ### 1.3 — Grafo de Fluxo de Controle

```
                  ┌─────────────┐
                  │ N1          │
                  │ Início      │
                  │ desconto=0  │
                  └──────┬──────┘
                         │
                         ▼
                  ┌─────────────┐
              ┌──▶│ N2          │
              │   │ valor>=500? │
              │   └──┬─────┬────┘
              │      │V    │F
              │      ▼     │
              │  ┌───────┐ │
              │  │ N3    │ │
              │  │desc=10│ │
              │  └───┬───┘ │
              │      │     │
              │      └──┬──┘
              │         ▼
              │   ┌─────────────┐
              │   │ N4          │
              │   │ clienteVip? │
              │   └──┬─────┬────┘
              │      │V    │F
              │      ▼     │
              │  ┌───────┐ │
              │  │ N5    │ │
              │  │ +5%   │ │
              │  └───┬───┘ │
              │      │     │
              │      └──┬──┘
              │         ▼
              │   ┌──────────────────┐
              │   │ N6               │
              │   │ !pagamento       │
              │   │ aprovado?        │
              │   └────┬────────┬────┘
              │        │V       │F
              │        ▼        ▼
              │   ┌────────┐ ┌──────────────┐
              │   │ N7     │ │ N8           │
              │   │ return │ │ calcula      │
              │   │ recusado│ │ valorFinal  │
              │   └────────┘ └──────┬───────┘
              │                     ▼
              │               ┌──────────────┐
              │               │ N9           │
              │               │ return       │
              │               │ aprovado     │
              │               └──────────────┘
```

 ### 1.4 — Arestas

 As **11 arestas** são:

 1. `N1 → N2`
2. `N2 → N3` — V
3. `N2 → N4` — F
4. `N3 → N4`
5. `N4 → N5` — V
6. `N4 → N6` — F
7. `N5 → N6`
8. `N6 → N7` — V
9. `N6 → N8` — F
10. `N8 → N9`
11. `N7` e `N9` → fim do método

 ### 1.5 — Número de nós e arestas

```
N = 9
E = 11
```

 ### 1.6 — Complexidade ciclomática

```
V(G) = E - N + 2

V(G) = 11 - 9 + 2

V(G) = 4
```

 **Complexidade ciclomática = 4.**

 ### 1.7 — Conferência pelo número de decisões

 O código possui **3 decisões**:

```
V(G) = número de decisões + 1

V(G) = 3 + 1

V(G) = 4
```

 Portanto, o resultado está correto.

 ### 1.8 — Base de caminhos independentes

 Uma base possível é:

 - **P1:** `N1 → N2(F) → N4(F) → N6(F) → N8 → N9`
- **P2:** `N1 → N2(V) → N3 → N4(F) → N6(F) → N8 → N9`
- **P3:** `N1 → N2(F) → N4(V) → N5 → N6(F) → N8 → N9`
- **P4:** `N1 → N2(F) → N4(F) → N6(V) → N7`

 ### 1.9 — Valores para cada caminho

 | Caminho | `valor` | `clienteVip` | `pagamentoAprovado` | Resultado |
| --- | --- | --- | --- | --- |
| P1 | 300 | `false` | `true` | `PEDIDO APROVADO: 300.0` |
| P2 | 600 | `false` | `true` | `PEDIDO APROVADO: 540.0` |
| P3 | 300 | `true` | `true` | `PEDIDO APROVADO: 285.0` |
| P4 | 300 | `false` | `false` | `PAGAMENTO RECUSADO` |

### 1.10 — Combinações possíveis

 Como existem 3 condições booleanas:

```
2³ = 8 combinações
```

 As combinações são:

 | `valor >= 500` | `clienteVip` | `pagamentoAprovado` |
| --- | --- | --- |
| F | F | F |
| F | F | V |
| F | V | F |
| F | V | V |
| V | F | F |
| V | F | V |
| V | V | F |
| V | V | V |

Portanto, existem **8 combinações possíveis**.

 ### 1.11 — Diferença entre combinações e complexidade ciclomática

 A complexidade ciclomática não representa todas as combinações possíveis das condições.

 - **Combinações possíveis:** 8
- **Caminhos independentes:** 4
- **Complexidade ciclomática:** 4

 ### 1.12 — Efeito do `return` antecipado

 Quando `!pagamentoAprovado` é verdadeiro, o fluxo segue:

```
N6 → N7 → fim
```

 O método é encerrado imediatamente e os nós `N8` e `N9` não são executados.

 ### 1.13 — Cálculo de `valorFinal`

 Não é possível calcular `valorFinal` quando o pagamento não foi aprovado.

 O fluxo é:

```
pagamentoAprovado = false
        ↓
       N6
        ↓
       N7
        ↓
      fim
```

 Portanto, o cálculo de `valorFinal` em **N8** só acontece quando `pagamentoAprovado = true`.

---

 ## exercício 2 \- Análise de leituras de temperatura

 ### 2.1 — Blocos básicos

 - **N1:** Início, `alertas = 0` e `i = 0`
- **N2:** `while (i < temperaturas.length)`
- **N3:** `if (temperaturas[i] < 0)`
- **N4:** `alertas += 2`
- **N5:** `else if (temperaturas[i] > 35)`
- **N6:** `alertas++`
- **N7:** `i++`
- **N8:** `return alertas`

 ### 2.2 — Decisões

 - **D1:** `i < temperaturas.length`
- **D2:** `temperaturas[i] < 0`
- **D3:** `temperaturas[i] > 35`

 Total: **3 decisões**.

### 2.3 — Grafo de Fluxo de Controle

```
                    ┌────────────────────┐
                    │ N1                 │
                    │ alertas = 0        │
                    │ i = 0              │
                    └─────────┬──────────┘
                              │
                              ▼
                    ┌────────────────────┐
                 ┌─▶│ N2                 │
                 │  │ i < length ?       │
                 │  └──────┬───────┬─────┘
                 │         │ V     │ F
                 │         ▼       │
                 │  ┌────────────┐ │
                 │  │ N3         │ │
                 │  │ temp < 0 ? │ │
                 │  └──┬─────┬───┘ │
                 │     │ V   │ F   │
                 │     ▼     ▼     │
                 │  ┌──────┐ ┌────────────┐
                 │  │ N4   │ │ N5         │
                 │  │+2    │ │ temp > 35? │
                 │  └──┬───┘ └──┬────┬────┘
                 │     │       V│    │F
                 │     │        ▼    │
                 │     │      ┌────┐ │
                 │     │      │ N6 │ │
                 │     │      │ +1 │ │
                 │     │      └─┬──┘ │
                 │     │        │    │
                 │     └────┬────┘    │
                 │          ▼         │
                 │    ┌────────────┐  │
                 │    │ N7         │◀─┘
                 │    │ i++        │
                 │    └─────┬──────┘
                 │          │
                 └──────────┘
                            │
                            │
                 F          ▼
             ┌────────────────────┐
             │ N8                 │
             │ return alertas     │
             └────────────────────┘
```
 ### 2.4 — Fluxos do laço

 - Temperatura negativa: `N3(V) → N4 → N7`
- Temperatura acima de 35: `N3(F) → N5(V) → N6 → N7`
- Temperatura entre 0 e 35: `N3(F) → N5(F) → N7`
- Retorno do laço: `N7 → N2`
- Saída do laço: `N2(F) → N8`

 ### 2.5 — Número de nós e arestas

```
N = 8
E = 10
```

 ### 2.6 — Complexidade ciclomática

 Pela fórmula:

```
V(G) = E - N + 2
V(G) = 10 - 8 + 2
V(G) = 4
```

 ### 2.7 — Conferência

 Existem 3 decisões:

```
V(G) = decisões + 1
V(G) = 3 + 1
V(G) = 4
```

 Portanto, a complexidade ciclomática é **4**.

 ### 2.8 — Caminhos independentes

 - **P1:** `N1 → N2(F) → N8`
- **P2:** `N1 → N2(V) → N3(V) → N4 → N7 → N2(F) → N8`
- **P3:** `N1 → N2(V) → N3(F) → N5(V) → N6 → N7 → N2(F) → N8`
- **P4:** `N1 → N2(V) → N3(F) → N5(F) → N7 → N2(F) → N8`

 ### 2.9 — Entradas e resultados

 - **P1:** `temperaturas = {}` → retorna **0**
- **P2:** `temperaturas = {-5}` → retorna **2**
- **P3:** `temperaturas = {40}` → retorna **1**
- **P4:** `temperaturas = {20}` → retorna **0**

 ### 2.10 — Importância do retorno do laço

 A aresta `N7 → N2` representa a repetição do `while`. Depois de processar cada temperatura, `i` é incrementado e a condição é testada novamente.

 Sem essa aresta, o CFG não representaria corretamente as várias iterações do laço.

 ### 2.11 — Questões para discussão

 - **Vetor com várias temperaturas:** pode repetir partes do grafo a cada elemento processado.
- **Sair sem acessar o vetor:** vetor vazio (`{}`).
- **Valor 0:** testa a fronteira entre negativo e não negativo.
- **Valor 35:** testa a fronteira da condição `> 35`; como é `35 > 35` falso, não gera alerta.
- **`else if` como nova decisão:** porque existe uma segunda condição (`> 35`) que também possui saída verdadeira e falsa.