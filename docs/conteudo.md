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

### Day 03

- Bibliotecas/escopo do dia:
  - NumPy
  - Matplotlib (uso mínimo: histograma)
- Tópicos usados:
  - RNG moderno e reprodutível: `np.random.default_rng(seed=...)`
  - Uniforme em [0, 1): `rng.random(size=...)`
  - Inteiros: `rng.integers(low, high, size=...)` (nota: `high` é exclusivo)
  - Normal padrão: `rng.standard_normal(n)`
  - Amostragem por escolha: `rng.choice(itens, size=..., replace=...)`
  - Visualização mínima: `plt.hist(...)` + `plt.show()`
- Habilidades demonstradas:
  - Gerar arrays aleatórios com shape definido e seed
  - Produzir histograma simples para inspeção de distribuição
  - Gerar amostras categóricas a partir de um conjunto
- Dificuldades/alertas observados:
  - Limites em `rng.integers`: confusão de inclusive/exclusivo no parâmetro `high`
- Observações de calibragem (para próximos desafios):
  - Sempre validar range pedido com `min/max` quando for requisito
  - Checar `shape`/`dtype` dos arrays gerados quando solicitado

---

#### Day 03 (Addendum — day_03_gpt)

- Ampliação praticada (mantendo o escopo do Day 03):
  - Reprodutibilidade forte com `default_rng`: duas instâncias com o mesmo seed geram arrays idênticos (prova por igualdade)
  - Transformação aritmética de uniforme: `rng.random` em [0,1) → escala + deslocamento para [a,b)
  - Inteiros com faixa controlada e validação objetiva do range (reforço do `high` exclusivo)
  - Composição 2D misturando floats e ints e evidência de promoção de tipo (`dtype` → float)
  - Casting para `int64` e evidência de truncamento (float → int)
  - Amostragem categórica via `rng.choice` com códigos numéricos (matriz 2D)
  - Separação de “fontes de aleatoriedade” por seed (SEED_A vs SEED_B) para ruído

- Dificuldades/alertas observados no day_03_gpt:
  - Range em `rng.integers`: ajuste fino do “inclusive/exclusivo” ainda oscilou
  - Auditoria: cuidados com `dtype` como string e mapeamento correto das chaves (evitar erro de concatenação por falta de vírgula)

---

### Day 04

- Bibliotecas/escopo do dia:
  - NumPy
  - Matplotlib (histograma + scatter 3D)

- Tópicos usados:
  - RNG reprodutível com `np.random.default_rng(seed=...)`
  - Geração de inteiros com `rng.integers(low, high, size=...)` (high exclusivo)
  - Broadcasting em operações vetorizadas: `np.add(arr1, arr2)` com shapes (2,3) e (1,3)
  - Produto vetorial/matricial: `np.dot(...)` com uso de transpose para compatibilizar shapes
  - Histograma de inteiros discretos com `plt.hist` e bins alinhados (via `np.arange`)
  - Estatística discreta: média (`arr.mean()`), contagem por valor com `np.bincount`, moda via `argmax`
  - Array 3D com `rng.random(shape)` e visualização 3D usando índices (`np.indices`) + `ravel` + `scatter`
  - Flatten/consulta de não-zero: `np.flatnonzero` (retorna índices)

- Habilidades demonstradas:
  - Aplicar broadcasting corretamente e interpretar o shape resultante
  - Executar dot product ajustando dimensões com transpose
  - Construir histograma coerente para dados inteiros discretos
  - Extrair moda com abordagem eficiente (`bincount + argmax`)
  - Preparar dados de um volume 3D para plot 3D (índices + valores)

- Dificuldades/alertas observados:
  - Limites em `rng.integers`: faixa “10..20” ficou desalinhada por escolha de `low/high`
  - Estatística pedida vs entregue: mediana foi solicitada e não calculada
  - Não-zero: uso de `flatnonzero` retorna índices, não os valores não-zero

- Observações de calibragem (para próximos desafios):
  - Sempre explicitar a interpretação do range (inclusive/exclusivo) e validar com `min/max`
  - Diferenciar “índices” vs “valores” ao filtrar arrays (máscara vs `flatnonzero`)
  - Quando houver estatística descritiva, garantir que a métrica pedida foi de fato calculada

---

#### Day 04 (Addendum — day_04_gpt)

- Ampliação praticada (sem sair do escopo do Day 04):
  - Transformação aritmética de uniforme: `rng.random` em [0,1) → escala + deslocamento para uma faixa alvo ([50,70))
  - Calibração por broadcasting com offsets negativos em shape (1, n) aplicado sobre matriz (m, n)
  - Pipeline “calibrated → score”: vetor de pesos (`standard_normal`) + produto matricial (`@`) gerando score 1D
  - Estatística aplicada ao score: mediana + “modo” via discretização (`astype(int64)`) e contagem (`bincount`) com cuidado para valores negativos (shift)
  - Log esparso gerado via `choice` com pool enviesado a zeros, com extração separada de:
    - valores não-zero (máscara)
    - posições (ex.: `argwhere`)

- Dificuldades/alertas observados no day_04_gpt:
  - Moda com `bincount` em dados discretizados negativos: precisa deslocar para não-negativo; `abs` não preserva corretamente a moda original
  - Evidências: qualquer forma que “apareça na saída” vale (print ou última expressão da célula); padronizar isso para evitar ruído de correção

---
