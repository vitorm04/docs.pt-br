---
title: 'Exceções: A função invalidArg'
description: Saiba como o F# 'invalidArg' função gera uma exceção de argumento.
ms.date: 05/16/2016
ms.openlocfilehash: 1f0cbc9b7e805822544d6d54bc1fc69adf82967a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645486"
---
# <a name="exceptions-the-invalidarg-function"></a>Exceções: A função invalidArg

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

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: O `try...with` expressão](the-try-with-expression.md)
- [Exceções: O `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: a função `raise`](the-raise-function.md)
- [Exceções: O `failwith` função](the-failwith-function.md)
