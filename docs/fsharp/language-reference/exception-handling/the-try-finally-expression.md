---
title: 'Exceções: a expressão try...finally (F#)'
description: "Saiba como o F # ' try... finally' que permite executar código de limpeza, mesmo se um bloco de código gera uma exceção."
ms.date: 05/16/2016
ms.openlocfilehash: a5fdec7b3986fc9a85c34b08d20dc31947c92b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563487"
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
