---
title: "Expressões lambda: a palavra-chave fun (F#)"
description: "Saiba como usar a palavra-chave F # 'fun' para definir uma expressão lambda, que é uma função anônima."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e5d3565c-d7cc-433f-a619-886ed92523a7
ms.openlocfilehash: 09f1c1787bbb4b86ec40f9e973e08104919631aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-the-fun-keyword-f"></a>Expressões lambda: a palavra-chave fun (F#)

O `fun` palavra-chave é usada para definir uma expressão lambda, ou seja, uma função anônima.


## <a name="syntax"></a>Sintaxe

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a>Comentários
O *a lista de parâmetros* normalmente é constituído de nomes e, opcionalmente, tipos de parâmetros. Geralmente, o *a lista de parâmetros* pode ser composto de quaisquer padrões F #. Para obter uma lista completa dos padrões possíveis, consulte [correspondência de padrões](../pattern-matching.md). Listas de parâmetros válidos incluem os exemplos a seguir.

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
Expressões lambda são especialmente úteis quando você deseja executar operações em uma lista ou outra coleção e para evitar o trabalho extra de definição de uma função. Muitas funções de biblioteca F # levam valores como argumentos de função e é especialmente conveniente ao usar uma expressão lambda nesses casos. O código a seguir se aplica a uma expressão lambda para elementos de uma lista. Nesse caso, a função anônima adiciona 1 a cada elemento de uma lista.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a>Consulte também
[Funções](index.md)
