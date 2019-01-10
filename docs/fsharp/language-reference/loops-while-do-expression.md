---
title: 'Loops: expressão while...do'
description: Veja como o while... Faça expressão é usada para uma execução iterativa (loop) enquanto uma condição de teste especificado é true.
ms.date: 05/16/2016
ms.openlocfilehash: d2a77e0bfefe3b6b026012e6b2938ba670326bcf
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613005"
---
# <a name="loops-whiledo-expression"></a>Loops: expressão while...do

O `while...do` expressão é usada para uma execução iterativa (loop) enquanto uma condição de teste especificado é true.

## <a name="syntax"></a>Sintaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Comentários

O *expressão de teste* é avaliada; se ele estiver `true`, o *corpo da expressão* é executado e a expressão é avaliada novamente. O *corpo da expressão* deve ter tipo `unit`. Se a expressão de teste for `false`, o término da iteração.

O exemplo a seguir ilustra o uso do `while...do` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, a última delas é 10.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Você pode usar `while...do` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `while...do` expressão é usada. Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Loops: `for...in` Expressão](loops-for-in-expression.md)
- [Loops: `for...to` Expressão](loops-for-to-expression.md)