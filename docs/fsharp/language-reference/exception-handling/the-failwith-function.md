---
title: 'Exceções: a função failwith (F#)'
description: "Saiba como a função 'failwith' gera uma exceção do F #."
ms.date: 05/16/2016
ms.openlocfilehash: 69a2eb69e0157d3bde8cb8884cb0ae960634dddc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784407"
---
# <a name="exceptions-the-failwith-function"></a>Exceções: a função failwith

O `failwith` função gerará uma exceção do F #.

## <a name="syntax"></a>Sintaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Comentários

O *sequência de mensagem de erro* na sintaxe anterior é uma cadeia de caracteres literal ou um valor do tipo `string`. Ele se torna o `Message` propriedade da exceção.

A exceção que é gerada pelo `failwith` é um `System.Exception` exceção, que é uma referência que tem o nome `Failure` no código F #. O código a seguir ilustra o uso de `failwith` para lançar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: a expressão `try...with`](the-try-with-expression.md)
- [Exceções: a expressão `try...finally`](the-try-finally-expression.md)
- [Exceções: a função `raise`](the-raise-function.md)
