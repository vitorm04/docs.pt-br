---
title: 'Expressões lambda: A palavra-chave Fun'
description: Saiba como usar a F# palavra-chave ' Fun ' para definir uma expressão lambda, que é uma função anônima.
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630668"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Expressões lambda: A palavra-chaveF#Fun ()

A `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.

## <a name="syntax"></a>Sintaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Comentários

A *lista de parâmetros* normalmente consiste em nomes e, opcionalmente, tipos de parâmetros. Em geral, a *lista de parâmetros* pode ser composta de qualquer F# padrão. Para obter uma lista completa de padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md). As listas de parâmetros válidos incluem os exemplos a seguir.

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

A *expressão* é o corpo da função, a última expressão que gera um valor de retorno. Exemplos de expressões lambda válidas incluem o seguinte:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a>Usando Expressões Lambda

As expressões lambda são especialmente úteis quando você deseja executar operações em uma lista ou em outra coleção e deseja evitar o trabalho extra de definir uma função. Muitas F# funções de biblioteca usam valores de função como argumentos e podem ser especialmente convenientes para usar uma expressão lambda nesses casos. O código a seguir aplica uma expressão lambda a elementos de uma lista. Nesse caso, a função anônima adiciona 1 a todos os elementos de uma lista.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
