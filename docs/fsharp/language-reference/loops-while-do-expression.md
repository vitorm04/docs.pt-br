---
title: 'Loops: expressão while...do'
description: Veja como o While... a expressão do é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630757"
---
# <a name="loops-whiledo-expression"></a>Loops: expressão while...do

A `while...do` expressão é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.

## <a name="syntax"></a>Sintaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Comentários

A *expressão de teste* é avaliada; Se for `true`, a *expressão Body* será executada e a expressão de teste será avaliada novamente. A *expressão Body* deve ter o tipo `unit`. Se a expressão de teste `false`for, a iteração terminará.

O exemplo a seguir ilustra o uso da `while...do` expressão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, o último deles é 10.

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Você pode usar `while...do` em expressões de sequência e outras expressões de computação, caso em que uma versão personalizada `while...do` da expressão é usada. Para obter mais informações, consulte [Sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de computação](computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Loops `for...in`Expressão](loops-for-in-expression.md)
- [Loops `for...to`Expressão](loops-for-to-expression.md)
