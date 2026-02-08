# Analista de Dados em 50 Dias — Conteúdo Liberado (conteudo.md)

Este arquivo é a “fonte de verdade” do que já foi efetivamente usado/aprendido nos challenges.
Ele NÃO é uma lista de tudo que existe no day_01 (teoria). O que libera conteúdo é o avanço por day_xx (prática).

Regras operacionais:

- Sempre que um day_xx for corrigido e receber nota, o GPT gera um BLOCO novo para ser colado em “Registro por dia”.
- Antes de gerar o day_xx_gpt, o GPT deve ler a versão latest deste arquivo.
- Pode incluir sinais de domínio/dificuldade para calibrar desafios futuros (sem liberar conteúdo futuro).

---

## Baseline permanente (sempre liberado)

- Python puro: LIBERADO (nível avançado do Bruno; não é foco de “nota por sintaxe”, e sim qualidade/clareza).

---

## Progressão de bibliotecas (informativo; não libera conteúdo sozinho)

- Ordem planejada: NumPy -> Pandas -> Matplotlib -> Seaborn -> Sklearn
- Observação: uma biblioteca só é considerada “liberada para cobrança” quando aparecer no day_xx (prática) e for registrada abaixo.

---

## Registro por dia (source-of-truth)

### Day 01 (Teoria)

- Status: teoria/base (não conta como avanço prático).
- Conteúdo: (será atualizado por você no day_01 ao longo do projeto, mas não “libera” cobrança automaticamente).

---

### Days práticos (a partir do Day 02)

> Instrução de atualização:
>
> - O GPT sempre vai gerar um bloco inteiro no formato abaixo para você colar como novo “Day XX”.
> - Cada bloco deve conter apenas o que foi efetivamente usado/exigido no day_xx corrigido.

#### Template de bloco (referência)

### Day XX

- Bibliotecas/escopo do dia:
  - (ex.: NumPy)
- Tópicos usados:
  - ...
- Habilidades demonstradas:
  - ...
- Dificuldades/alertas observados:
  - ...
- Observações de calibragem (para próximos desafios):
  - ...

---

### Day 02

- Bibliotecas/escopo do dia:
  - NumPy

- Tópicos usados:
  - Criação de `ndarray` 1D e 2D com `np.array`
  - Inspeção de propriedades: `shape`, `ndim`, `dtype` (e uso de tamanho via `len()`/`size`)
  - Slicing para reversão (`[::-1]`)
  - Conversão de tipo com `astype(np.int64)` e implicações (perda de parte decimal)
  - Promoção de tipo (ints + floats resultam em `dtype` promovido, tipicamente `float`)

- Habilidades demonstradas:
  - Montagem e inspeção correta de estruturas NumPy
  - Uso adequado de slicing vetorizado
  - Casting explícito com `astype` e validação do resultado

- Dificuldades/alertas observados:
  - Conceito: confusão entre “misturar valores de tipos diferentes na criação” vs “array manter tipos diferentes internamente” (NumPy mantém `dtype` homogêneo; mistura promove o tipo)
  - Boas práticas: preferir `arr.size` quando o objetivo é “quantidade total de elementos”

- Observações de calibragem (para próximos desafios):
  - Cobrar com mais rigor entendimento de `dtype`, promoção de tipo e consequências de casting (principalmente float → int)
  - Incentivar escolhas idiomáticas (`arr.size`, evitar `np.array()` redundante ao retornar slicing)

---
