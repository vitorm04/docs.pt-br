---
title: "Exceções: a expressão try...finally (F#)"
description: "Saiba como o F # ' try... finally' que permite executar código de limpeza, mesmo se um bloco de código gera uma exceção."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a>Exceções: a expressão try...finally

O `try...finally` expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.


## <a name="syntax"></a>Sintaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Comentários
O `try...finally` expressão pode ser usada para executar o código em *expression2* na sintaxe anterior, independentemente se uma exceção é gerada durante a execução de *expression1*.

O tipo de *expression2* não contribuem para o valor da expressão de inteiro; o tipo retornado quando não ocorrer uma exceção é o último valor *expression1*. Quando ocorre uma exceção, nenhum valor será retornado e o fluxo de controle transfere para o manipulador de exceção correspondente próximo a pilha de chamadas. Se nenhum manipulador de exceção é encontrada, o programa será encerrado. Antes do código em um manipulador de correspondência é executado ou o programa é encerrado, o código de `finally` ramificação é executada.

O código a seguir demonstra o uso de `try...finally` expressão.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

A saída para o console é o seguinte.

```
Closing stream
Exception handled.
```

Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa foi tratada e o arquivo `test.txt` contém o texto `test1`, que indica que os buffers foram liberados e gravados no disco, embora a exceção transferidos controle ao manipulador de exceção externa.

Observe que o `try...with` construção é uma construção separada do `try...finally` construir. Portanto, se seu código requer um `with` bloco e um `finally` bloco, você precisa aninhar as duas construções, como no exemplo de código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos, **try... finally** expressões podem ter uma implementação personalizada. Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).


## <a name="see-also"></a>Consulte também
[Tratamento de Exceção](index.md)

[Exceções: a expressão `try...with`](the-try-with-expression.md)
