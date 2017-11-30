---
title: "Exceções: a função failwith (F#)"
description: "Saiba como a função 'failwith' gera uma exceção F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a>Exceções: a função failwith

O `failwith` função gera uma exceção F #.


## <a name="syntax"></a>Sintaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Comentários
O *sequência de mensagem de erro* na sintaxe anterior é uma cadeia de caracteres literal ou um valor do tipo `string`. Ele se torna o `Message` propriedade da exceção.

A exceção que é gerada pelo `failwith` é um `System.Exception` exceção, que é uma referência que tem o nome `Failure` no código F #. O código a seguir ilustra o uso de `failwith` para lançar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>Consulte também
[Tratamento de Exceção](index.md)

[Tipos de Exceção](exception-types.md)

[Exceções: a expressão `try...with`](the-try-with-expression.md)

[Exceções: a expressão `try...finally`](the-try-finally-expression.md)

[Exceções: a função `raise`](the-raise-function.md)
