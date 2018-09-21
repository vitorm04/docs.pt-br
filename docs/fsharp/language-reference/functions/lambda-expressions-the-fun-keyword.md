---
title: 'Expressões lambda: a palavra-chave fun (F#)'
description: "Saiba como usar a palavra-chave F # 'divertido' para definir uma expressão lambda, que é uma função anônima."
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525513"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Expressões lambda: a palavra-chave fun (F#)

O `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.

## <a name="syntax"></a>Sintaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Comentários

O *lista de parâmetros* normalmente consiste em nomes e, opcionalmente, tipos de parâmetros. De modo geral, o *lista de parâmetros* pode ser composto de quaisquer padrões em F #. Para obter uma lista completa de padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md). Listas de parâmetros válidos incluem os exemplos a seguir.

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

O *expressão* é o corpo da função, a última expressão que gera um valor de retorno. Exemplos de expressões lambda válidos incluem o seguinte:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Usando Expressões Lambda

Expressões lambda são especialmente úteis quando você deseja realizar operações em uma lista ou outra coleção e quiser evitar o trabalho extra de definir uma função. Muitas funções de biblioteca F # levam valores como argumentos de função e pode ser especialmente conveniente usar uma expressão lambda nesses casos. O código a seguir aplica uma expressão lambda para elementos de uma lista. Nesse caso, a função anônima adiciona 1 a cada elemento de uma lista.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
