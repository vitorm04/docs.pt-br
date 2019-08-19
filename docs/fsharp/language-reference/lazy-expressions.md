---
title: Expressões lentas
description: Saiba como F# as expressões lentas podem melhorar o desempenho de seus aplicativos e bibliotecas.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630742"
---
# <a name="lazy-expressions"></a>Expressões lentas

As *expressões lentas* são expressões que não são avaliadas imediatamente, mas, em vez disso, são avaliadas quando o resultado é necessário. Isso pode ajudar a melhorar o desempenho do seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *expression* é o código que é avaliado somente quando um resultado é necessário e o *identificador* é um valor que armazena o resultado. O valor é do tipo [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), onde o tipo real usado para `'T` é determinado a partir do resultado da expressão.

As expressões lentas permitem melhorar o desempenho restringindo a execução de expressões para apenas as situações em que um resultado é necessário.

Para forçar a execução das expressões, você chama o método `Force`. `Force`faz com que a execução seja executada apenas uma vez. As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não executam nenhum código.

O código a seguir ilustra o uso de expressões lentas e o `Force`uso de. Nesse código, o tipo `result` de é `Lazy<int>`e o `Force` método retorna um `int`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

A avaliação lenta, mas não `Lazy` o tipo, também é usada para sequências. Para obter mais informações, consulte [sequences](sequences.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Módulo LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
