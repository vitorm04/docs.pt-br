---
title: 'Exceções: A função invalidArg'
description: Saiba como a F# função ' InvalidArg ' gera uma exceção de argumento.
ms.date: 05/16/2016
ms.openlocfilehash: 6b1c5fdb5a541da336977d3a67d471302edb36b6
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083020"
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

```console
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
