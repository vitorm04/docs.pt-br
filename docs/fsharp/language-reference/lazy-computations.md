---
title: Computações lentas (F#)
description: 'Saiba como as computações lentas do F # podem melhorar o desempenho de seus aplicativos e bibliotecas.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698202"
---
# <a name="lazy-computations"></a>Computações lentas

*Computações lentas* são cálculos que não são avaliados imediatamente, mas em vez disso, são avaliados quando o resultado é necessária. Isso pode ajudar a melhorar o desempenho do seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado. O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), em que o valor real de tipo que é usado para `'T` é determinado a partir do resultado da expressão.

Computações lentas que você possa melhorar o desempenho, restringindo a execução de um cálculo para somente essas situações em que um resultado é necessária.

Para forçar o cálculo a ser executada, você chama o método `Force`. `Force` faz com que a execução a ser executada apenas uma vez. As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não execute qualquer código.

O código a seguir ilustra o uso de computação lenta e o uso de `Force`. Nesse código, o tipo de `result` está `Lazy<int>`e o `Force` método retorna um `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

A avaliação lenta, mas não o `Lazy` de tipo, também é usado para as sequências. Para obter mais informações, consulte [sequências](sequences.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulo LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
