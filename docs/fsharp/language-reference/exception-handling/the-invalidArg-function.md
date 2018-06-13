---
title: 'Exceções: a função invalidArg (F#)'
description: "Saiba como a função 'invalidArg' F # gera uma exceção de argumento."
ms.date: 05/16/2016
ms.openlocfilehash: 43e1b6f3f36774ac50aeff147f75f133d6e3e5dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564502"
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
