---
title: "Computações lentas (F#)"
description: "Saiba como F # computações lentas podem melhorar o desempenho de aplicativos e bibliotecas."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a>Computações lentas

*Computações lentas* são cálculos que não são avaliados imediatamente, mas em vez disso, são avaliados quando o resultado é necessária. Isso pode ajudar a melhorar o desempenho do seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado. O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), onde o tipo que é usado para `'T` é determinado a partir do resultado da expressão.

Computações lentas permitem melhorar o desempenho, restringindo a execução de um cálculo para somente nas situações em que um resultado é necessária.

Para forçar o cálculo a ser executada, você pode chamar o método `Force`. `Force`faz com que a execução seja executada apenas uma vez. As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não executa qualquer código.

O código a seguir ilustra o uso de computação lenta e o uso de `Force`. Nesse código, o tipo de `result` é `Lazy<int>`e o `Force` método retorna um `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Avaliação lenta, mas não o `Lazy` digite, também é usado para as sequências. Para obter mais informações, consulte [sequências](sequences.md).

## <a name="see-also"></a>Consulte também

[Referência da Linguagem F#](index.md)

[Módulo LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
