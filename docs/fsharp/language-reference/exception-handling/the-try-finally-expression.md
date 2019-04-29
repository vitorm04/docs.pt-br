---
title: 'Exceções: A expressão try...finally'
description: Saiba como o F# ' try... finally' expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 24613185818c8ea30b27dcf639b22af320c4b401
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772691"
---
# <a name="exceptions-the-tryfinally-expression"></a>Exceções: A expressão try...finally

O `try...finally` expressão permite que você execute o código de limpeza, mesmo se um bloco de código gera uma exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Comentários

O `try...finally` expressão pode ser usada para executar o código na *expression2* na sintaxe anterior, independentemente de se uma exceção é gerada durante a execução da *expression1*.

O tipo de *expression2* não contribui para o valor da expressão inteira; o tipo retornado quando ocorre uma exceção é o último valor no *expression1*. Quando ocorre uma exceção, nenhum valor é retornado e o fluxo de controle transfere para o próximo manipulador de exceções correspondente a pilha de chamadas. Se nenhum manipulador de exceção é encontrada, o programa é encerrado. Antes do código em um manipulador correspondente é executado ou o programa é encerrado, o código a `finally` ramificação é executado.

O código a seguir demonstra o uso do `try...finally` expressão.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

A saída para o console é da seguinte maneira.

```
Closing stream
Exception handled.
```

Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa foi tratada e o arquivo `test.txt` contém o texto `test1`, que indica que os buffers foram liberados e gravados no disco, mesmo que a exceção transferidos o controle para o manipulador de exceção externa.

Observe que o `try...with` constructo é uma construção separada do `try...finally` construir. Portanto, se seu código exigir ambos um `with` bloco e um `finally` bloco, é necessário aninhar as duas construções, como no exemplo de código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos **try... finally** expressões podem ter uma implementação personalizada. Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Exceções: O `try...with` expressão](the-try-with-expression.md)