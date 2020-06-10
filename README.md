<div align="center">
    <h1>RegEX</h1>
    <img src="https://img.shields.io/github/last-commit/lucasquitan/regex">
    <img src="https://img.shields.io/github/stars/lucasquitan/regex">
</div>

# Conteúdo

- [Conteúdo](#conteúdo)
  - [História](#história)
    - [Definição](#definição)
    - [Origem](#origem)
    - [Teoria da Computação (Linguagens Formais)](#teoria-da-computação-linguagens-formais)
  - [Caracteres Especiais](#caracteres-especiais)
  - [Caracteres não visíveis](#caracteres-não-visíveis)
  - [Classes de caracteres](#classes-de-caracteres)
  - [Classes Opostas](#classes-opostas)
  - [Múltiplos Padrões](#múltiplos-padrões)
  - [Operadores de Repetição](#operadores-de-repetição)
  - [Grupos de Captura](#grupos-de-captura)
  - [Back References](#back-references)
  - [Âncoras](#âncoras)

---
## História

### Definição

No mundo da computação, uma **expressão regular** ou `Regex` (ou os estrangeirismos regex ou regexp, abreviação do inglês regular expression) provê uma forma concisa e flexível de identificar cadeias de caracteres de interesse, como caracteres particulares, palavras ou padrões de caracteres. Expressões regulares são escritas numa linguagem formal que pode ser interpretada por um processador de expressão regular, um programa que serve um gerador de analisador sintático ou examina o texto e identifica as partes que casam com a especificação dada.

Uma expressão regular (ou, um padrão) descreve um conjunto de cadeias de caracteres, de forma concisa, sem precisar listar todos os elementos do conjunto. Por exemplo, um conjunto contendo as cadeias `Handel`, `Händel` e `Haendel` pode ser descrito pelo padrão `H(ä|ae?)ndel`. A maioria dos formalismos provê pelo menos três operações para construir expressões regulares.


### Origem

A origem das expressões regulares está na teoria dos autômatos e na [teoria das linguagens formais](#teoria-da-computação-linguagens-formais), e ambas fazem parte da teoria da computação. Esses campos estudam modelos de computação (autômatos) e formas de descrição e classificação de linguagens formais. Na década de 1950, o matemático **Stephen Cole Kleene** descreveu tais modelos usando sua notação matemática chamada de "conjuntos regulares", formando a álgebra de Kleene.

### Teoria da Computação (Linguagens Formais)

Expressões regulares podem ser expressas através da teoria de linguagens formais. Elas consistem de constantes e operadores que denotam conjuntos de cadeias de caracteres e operações sobre esses conjuntos, respectivamente. Dado um **alfabeto finito** denotado por `Σ`, as seguintes constantes são definidas:

- **Conjunto Vazio** ∅:  Denotando o conjunto ∅
- **Cadeia Vazia** ε: Denotando ε. O conjunto é denotado por {ε}

De forma literal: Dado um a qualquer partencendo ao alfabeto Σ. Em outras palavras, temos `a ∈ Σ | Σ = {a}`.

Para mais informações e materiais sobre esse assunto, clique [aqui](https://cic.unb.br/~rezende/tc.html) e saiba mais. [**Teoria da Computação - UnB**]

## Caracteres Especiais

Alguns caracteres possuem um significado especial para o texto. Estes caracteres são:

`$, ^, *, (, ), +, {, }, [, ], \, |, ?, -,  .`

Para utilizarmos como caracteres normais, devemos utilizar o `\` antes deles.


## Caracteres não visíveis

- O tab é representado por `-Tab-`, mas na RegEx você deve usar `\t`
- A quebra de linha é representada por `-Quebra-de-Linha-`, mas na RegEx você deve usar `\n`
- A quebra de página é representada por `-Quebra-de-Pagina-`, mas na RegEx você deve usar `\f`
- O retorno é representada por `-Retorno-`, mas na RegEx você deve usar `\r`
- O tab vertical é representada por `-Tab-Vertical-`, mas na RegEx você deve usar `\x0B`
- O espaço em branco é representado por `-Espaço`-, mas você continua apenas apertando a barra de espaço.
- O padrão vazio é representado por `-Vazio-`, mas você simplesmente não escreve nada.

---

## Classes de caracteres

As classes de caracteres são sequecias que podem ser definidas entre **colchetes** `[]`

- A RegEx `[A-Z]` reconhece todas as letras maiúsculas.
- A RegEx `[A-Z0-9]` reconhece todas as letras maiúsculas e números.
- A RegEx `[f-h]` reconhece as letras f, g e h.

Existem classes específicas que são pré-definidas:

- A classe `\d` é equivalente à classe [0-9]
- A classe `\s` é equivalente à classe [ \t\n\x0B\f\r]
- A classe `\w` é equivalente à classe [a-zA-Z_0-9]
- A classe `.` reconhece todos os tipos de caracteres, exceto o \n.

> Por exemplo, a RegEx `\d\w` **reconhece** o padrão 9a e o 11, mas não reconhece o padrão a9.

## Classes Opostas

É possível determinar classes que não possuem determinados caracteres ou classes. Para isso, basta inserir `^` após o `[` que marca o início de uma classe.

> Para utilizar o oposto em classes pré-definidas, utilizamos o indicador em `Caixa Alta`.

- A RegEx `[^a]` reconhece qualquer caractere, exceto a.
- A RegEx `[^b-d]` reconhece qualquer caractere, exceto b, c e d.
- A RegEx `[^\d]` reconhece qualquer caractere, exceto 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9.
- A RegEx `\D` reconhece qualquer caractere que não seja 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9.

---

## Múltiplos Padrões

Uma forma simples de se especificar múltiplos padrões que uma RegEx deve reconhecer é utilizar o caractere `|` para separá-los.

- A RegEx `a|b` reconhece o padrão `a` e o `b`
- A RegEx `abc|a` reconhece o padrão `abc` e o `a`
- A RegEx `a|ab|ab`c reconhece o padrão `a`, o `ab` e o `abc`

---

## Operadores de Repetição

A idéia principal desses operadores é permitir que você defina um padrão específico que você espera que ocorra um determinado número de vezes.

- `?` determina que o que vier imediatamente antes dele deve aparecer 0 ou 1 vez na expressão.
- `*` determina que o que vier imediatamente antes dele deve aparecer 0 ou mais vezes na expressão.
- `+` determina que o que vier imediatamente antes dele deve aparecer 1 ou mais vezes na expressão.
- `{n}` determina que o que vier imediatamente antes dele deve aparecer exatamente n vezes na expressão.
- `{n,}` determina que o que vier imediatamente antes dele deve aparecer n ou mais vezes na expressão.
- `{n, m}` determina que o que vier imediatamente antes dele deve aparecer no mínimo n e no máximo m vezes na expressão.

> Não necessariamente será um caractere antes do operador. É permitido cadeias também.

---

## Grupos de Captura

Para definir um grupo de captura você utiliza os caracteres( e ) envolvendo o padrão de RegEx que você que capturar no seu texto.

- A RegEx `Assunto: (\w+)` reconhece o padrão `Assunto: importante` e captura **importante** no grupo `1`.
- A RegEx `(parametro=(\w+))` reconhece o padrão `parametro=legal` e captura **parametro**=**legal** no grupo `1` e `legal` no grupo 2.

---

## Back References

Back references é utilizado quando queremos conhecer um trecho previamente capturado (como o conteúdo entre duas tags, por exemplo).

Para utilizar uma **back reference**, utilizamos o caractere `\` seguido pelo número do grupo de captura que queremos referenciar. Vale lembrar que o grupo `0` é tudo que a RegEx encontrou. Então só faz sentido começarmos a referenciar a partir do `1`.

- A RegEx `(a)\1` reconhece o padrão aa
- A RegEx `<([^>]+)>[^<]+</\1>` reconhece o padrão` <b>abc</b>`, mas não reconhece o padrão `<b>abc</i>`
- A RegEx `(b+)\1` reconhece todas as sequências de `b` que tenham um número de caracteres **pares** (como bb, bbbb, etc)

---

## Âncoras

Âncoras servem para dar uma referência para as suas RegEx. Por exemplo, você pode querer reconhecer `tomate`, mas não querer reconhecer `o tomate`.

Para fazer isso, você pode usar um operador como o `^`, que âncora ao começo da linha, o `$` que âncora ao fim da linha e o `\b`, que ancora a qualquer coisa que não seja uma letra ou número.

- A RegEx `^tomate` reconhece o padrão `tomate`, mas não reconhece `o tomate`
- A RegEx `tomate$` reconhece o padrão `tomate` e `bom tomat`e, mas não reconhece `tomates`
- A RegEx `\btomate\b` reconhece o padrão `tomate` e `bom tomate` e `tomate gostoso`, mas não reconhece `tomates`

---

<p align="center">
    O conteúdo técnico desde documento foi retirado de <a href="http://aprenda.vidageek.net/aprenda/regex">VidaGeek.net</a>
</p>