---
title: Expressões de correspondência
description: Saiba como o F# expressão de correspondência fornece controle de ramificação com base na comparação de uma expressão com um conjunto de padrões.
ms.date: 04/19/2018
ms.openlocfilehash: 69ff8de1617e6b55d112d310bfcd8b2f967b6e8a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645208"
---
# <a name="match-expressions"></a>Expressões de correspondência

O `match` expressão fornece controle de ramificação com base na comparação de uma expressão com um conjunto de padrões.

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

As expressões de correspondência de padrão permitem a ramificação complexa com base na comparação de uma expressão de teste com um conjunto de padrões. No `match` expressão, o *expressão de teste* é comparado com cada padrão, por sua vez, e quando uma correspondência for encontrada, o correspondente *expressão de resultado* é avaliada e o valor resultante é retornado como o valor da expressão de correspondência.

A função mostrada na sintaxe anterior de correspondência de padrão é uma expressão lambda no qual padrão de correspondência é executada imediatamente no argumento. A correspondência de função mostrada na sintaxe anterior é equivalente ao seguinte.

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

Para obter mais informações sobre expressões lambda, consulte [expressões Lambda: O `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md).

O conjunto completo de padrões deve abranger todas as correspondências possíveis a variável de entrada. Frequentemente, você pode usar o padrão de curinga (`_`) como o último padrão para coincidir com quaisquer valores de entrada sem correspondência anteriormente.

O código a seguir ilustra algumas das maneiras em que o `match` expressão é usada. Para obter uma referência e exemplos de todos os padrões possíveis que podem ser usados, consulte [correspondência de padrões](pattern-matching.md).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>Proteções de padrões

Você pode usar um `when` cláusula para especificar uma condição adicional que a variável deve satisfazer para corresponder a um padrão. Essa cláusula é conhecida como um *proteger*. A expressão após a `when` palavra-chave não é avaliada, a menos que uma correspondência é feita para o padrão associado a essa protetor.

O exemplo a seguir ilustra o uso de uma proteção para especificar um intervalo numérico para um padrão de variável. Observe que várias condições são combinadas usando operadores boolianos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

Observe que como valores diferentes de literais não podem ser usados no padrão, você deve usar um `when` cláusula se você tiver alguma parte da entrada em relação a um valor de comparar. Isso é mostrado no código a seguir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

Observe que, quando um padrão de união é coberto por um protetor, a proteção se aplica ao **todos os** de padrões, não apenas o último deles. Por exemplo, considerando o código a seguir, o protetor `when a > 12` se aplica a ambos `A a` e `B a`:

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
