---
title: 'Exceções: A função failwith'
description: Saiba como a função ' failwith ' gera uma F# exceção.
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630330"
---
# <a name="exceptions-the-failwith-function"></a>Exceções: A função failwith

A `failwith` função gera uma F# exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Comentários

A *cadeia de caracteres de mensagem de erro* na sintaxe anterior é uma cadeia de caracteres literal ou um `string`valor do tipo. Ele se torna `Message` a propriedade da exceção.

A `failwith` exceção gerada pelo é uma `System.Exception` exceção, que é uma referência que tem o nome `Failure` no F# código. O código a seguir ilustra o uso `failwith` de para gerar uma exceção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: A `try...with` expressão](the-try-with-expression.md)
- [Exceções: A `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: a função `raise`](the-raise-function.md)
