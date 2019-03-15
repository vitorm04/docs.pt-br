---
title: Expressões lentas
description: Saiba como F# expressões lentas podem melhorar o desempenho de seus aplicativos e bibliotecas.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57853317"
---
# <a name="lazy-expressions"></a>Expressões lentas

*Expressões lentas* são expressões que não são avaliadas imediatamente, mas em vez disso, são avaliadas quando o resultado é necessária. Isso pode ajudar a melhorar o desempenho do seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado. O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), em que o valor real de tipo que é usado para `'T` é determinado a partir do resultado da expressão.

Expressões lentas permitem que você melhorar o desempenho, restringindo a execução de uma expressões para somente essas situações em que um resultado é necessária.

Para forçar as expressões a serem executadas, você chama o método `Force`. `Force` faz com que a execução a ser executada apenas uma vez. As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não execute qualquer código.

O código a seguir ilustra o uso de expressões lentas e o uso de `Force`. Nesse código, o tipo de `result` está `Lazy<int>`e o `Force` método retorna um `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

A avaliação lenta, mas não o `Lazy` de tipo, também é usado para as sequências. Para obter mais informações, consulte [sequências](sequences.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulo LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
