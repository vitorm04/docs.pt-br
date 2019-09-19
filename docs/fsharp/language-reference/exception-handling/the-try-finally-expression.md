---
title: 'Exceções: A expressão try...finally'
description: Saiba como o F# ' Try... Finally ' permite que você execute código de limpeza mesmo que um bloco de código gere uma exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083003"
---
# <a name="exceptions-the-tryfinally-expression"></a>Exceções: A expressão try...finally

A `try...finally` expressão permite que você execute o código de limpeza mesmo que um bloco de código gere uma exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Comentários

A `try...finally` expressão pode ser usada para executar o código em *expression2* na sintaxe anterior, independentemente de uma exceção ser gerada durante a execução de *expressão1*.

O tipo de *expression2* não contribui para o valor da expressão inteira; o tipo retornado quando uma exceção não ocorre é o último valor em *expression1*. Quando ocorre uma exceção, nenhum valor é retornado e o fluxo de controle é transferido para o próximo manipulador de exceção correspondente na pilha de chamadas. Se nenhum manipulador de exceção for encontrado, o programa será encerrado. Antes que o código em um manipulador correspondente seja executado ou o programa seja encerrado, o código `finally` na ramificação será executado.

O código a seguir demonstra o uso da `try...finally` expressão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

A saída para o console é a seguinte:

```console
Closing stream
Exception handled.
```

Como você pode ver na saída, o fluxo foi fechado antes que a exceção externa fosse tratada e o arquivo `test.txt` contém o texto `test1`, o que indica que os buffers foram liberados e gravados no disco, mesmo que a exceção seja transferida controle para o manipulador de exceção externa.

Observe que a `try...with` construção é uma construção separada `try...finally` da construção. Portanto, se o seu código exigir um `with` bloco e um `finally` bloco, você precisará aninhar as duas construções, como no exemplo de código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

No contexto de expressões de computação, incluindo expressões de sequência e fluxos de trabalho assíncronos, **tente...** as expressões finally podem ter uma implementação personalizada. Para obter mais informações, consulte [expressões de computação](../computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Exceções: A `try...with` expressão](the-try-with-expression.md)
