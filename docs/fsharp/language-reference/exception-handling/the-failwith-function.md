---
title: 'Exceções: A função failwith'
description: Saiba como a função 'failwith' gera um F# exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 08107966ddc2f55625347deb92d224b286df7761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641944"
---
# <a name="exceptions-the-failwith-function"></a>Exceções: A função failwith

O `failwith` função gera uma F# exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Comentários

O *sequência de mensagem de erro* na sintaxe anterior é uma cadeia de caracteres literal ou um valor do tipo `string`. Ele se torna o `Message` propriedade da exceção.

A exceção que é gerada pelo `failwith` é um `System.Exception` exceção, que é uma referência que tem o nome `Failure` em F# código. O código a seguir ilustra o uso de `failwith` para lançar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: O `try...with` expressão](the-try-with-expression.md)
- [Exceções: O `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: a função `raise`](the-raise-function.md)
