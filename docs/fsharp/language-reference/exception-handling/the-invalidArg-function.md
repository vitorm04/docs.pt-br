---
title: 'Exceções: a função invalidArg (F#)'
description: "Saiba como a função 'invalidArg' F # gera uma exceção de argumento."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: fc7b1d25adf71bc1704a3f2db4359006f0ba1670
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-invalidarg-function"></a>Exceções: a função invalidArg

O `invalidArg` função gera uma exceção de argumento.


## <a name="syntax"></a>Sintaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Comentários
O nome do parâmetro na sintaxe anterior é uma cadeia de caracteres com o nome do parâmetro cujo argumento era inválido. O *sequência de mensagem de erro* é uma cadeia de caracteres literal ou um valor do tipo `string`. Ele se torna o `Message` propriedade do objeto de exceção.

A exceção gerada pelo `invalidArg` é um `System.ArgumentException` exceção. O código a seguir ilustra o uso de `invalidArg` para lançar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

A saída é o seguinte, seguido por um rastreamento de pilha (não mostrado).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Consulte também
[Tratamento de Exceção](index.md)

[Tipos de Exceção](exception-types.md)

[Exceções: a expressão `try...with`](the-try-with-expression.md)

[Exceções: a expressão `try...finally`](the-try-finally-expression.md)

[Exceções: a função `raise`](the-raise-function.md)

[Exceções: a função `failwith`](the-failwith-function.md)
