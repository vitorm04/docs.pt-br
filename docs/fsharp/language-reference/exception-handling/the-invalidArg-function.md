---
title: 'Exceções: A função invalidArg'
description: Saiba como a F# função ' InvalidArg ' gera uma exceção de argumento.
ms.date: 05/16/2016
ms.openlocfilehash: 010dbfe313f539093b4ee7a19984ef54500b072d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630300"
---
# <a name="exceptions-the-invalidarg-function"></a>Exceções: A função invalidArg

A `invalidArg` função gera uma exceção de argumento.

## <a name="syntax"></a>Sintaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Comentários

O parâmetro-Name na sintaxe anterior é uma cadeia de caracteres com o nome do parâmetro cujo argumento era inválido. A *cadeia de caracteres de mensagem de erro* é uma cadeia de caracteres literal ou `string`um valor do tipo. Ele se torna `Message` a propriedade do objeto de exceção.

A exceção gerada por `invalidArg` é uma `System.ArgumentException` exceção. O código a seguir ilustra o uso `invalidArg` de para gerar uma exceção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

A saída é a seguinte, seguida por um rastreamento de pilha (não mostrado).

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: A `try...with` expressão](the-try-with-expression.md)
- [Exceções: A `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: a função `raise`](the-raise-function.md)
- [Exceções: A `failwith` função](the-failwith-function.md)
