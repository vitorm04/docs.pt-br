---
title: Expressões de correspondência
description: Saiba como a F# expressão de correspondência fornece controle de ramificação baseado na comparação de uma expressão com um conjunto de padrões.
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627612"
---
# <a name="match-expressions"></a>Expressões de correspondência

A `match` expressão fornece controle de ramificação baseado na comparação de uma expressão com um conjunto de padrões.

## <a name="syntax"></a>Sintaxe

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>Comentários

As expressões de correspondência de padrões permitem ramificação complexa com base na comparação de uma expressão de teste com um conjunto de padrões. Na expressão, a *expressão de teste* é comparada com cada padrão por vez e quando uma correspondência é encontrada, a expressão de resultado correspondente é avaliada e o valor resultante é retornado como o valor da expressão de correspondência. `match`

A função de correspondência de padrões mostrada na sintaxe anterior é uma expressão lambda na qual o padrão correspondente é executado imediatamente no argumento. A função de correspondência de padrões mostrada na sintaxe anterior é equivalente à seguinte.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Para obter mais informações sobre expressões lambda, [consulte expressões lambda: A `fun` palavra](./functions/lambda-expressions-the-fun-keyword.md)-chave.

O conjunto completo de padrões deve abranger todas as possíveis correspondências da variável de entrada. Frequentemente, você usa o padrão de curinga`_`() como o último padrão para corresponder a qualquer valor de entrada não correspondente anteriormente.

O código a seguir ilustra algumas das maneiras em que a `match` expressão é usada. Para obter uma referência e exemplos de todos os padrões possíveis que podem ser usados, consulte [correspondência de padrões](pattern-matching.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Protege os padrões

Você pode usar uma `when` cláusula para especificar uma condição adicional que a variável deve satisfazer para corresponder a um padrão. Essa cláusula é conhecida como *proteção*. A expressão após a `when` palavra-chave não é avaliada, a menos que uma correspondência seja feita ao padrão associado a essa proteção.

O exemplo a seguir ilustra o uso de uma proteção para especificar um intervalo numérico para um padrão variável. Observe que várias condições são combinadas usando operadores boolianos.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Observe que, como valores diferentes de literais não podem ser usados no padrão, você deve usar `when` uma cláusula se precisar comparar alguma parte da entrada com relação a um valor. Isso é mostrado no código a seguir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Observe que, quando um padrão de União é coberto por uma proteção, a proteção se aplica a **todos** os padrões, não apenas ao último. Por exemplo, considerando o código a seguir, a `when a > 12` proteção se aplica `A a` a `B a`e:

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Padrões Ativos](active-patterns.md)
- [Correspondência Padrão](pattern-matching.md)
