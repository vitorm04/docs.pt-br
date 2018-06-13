---
title: 'Loops: expressão while...do (F#)'
description: Veja como o while... Faça expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true.
ms.date: 05/16/2016
ms.openlocfilehash: e3198246e44bbb11b226f04da6795f3da22626e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562226"
---
# <a name="loops-whiledo-expression"></a>Loops: expressão while...do

O `while...do` expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true.


## <a name="syntax"></a>Sintaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Comentários
O *expressão de teste* é avaliada; se for `true`, o *corpo da expressão* é executado e a expressão é avaliada novamente. O *corpo da expressão* deve ser do tipo `unit`. Se a expressão de teste é `false`, as extremidades de iteração.

O exemplo a seguir ilustra o uso do `while...do` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, a última delas é 10.

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
Você pode usar `while...do` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `while...do` expressão é usada. Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Loops: `for...in` expressão](loops-for-in-expression.md)

[Loops: `for...to` expressão](loops-for-to-expression.md)
