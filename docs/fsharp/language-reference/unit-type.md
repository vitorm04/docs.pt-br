---
title: Tipo unit
description: Saiba como o F# tipo de "unidade" geralmente é usado para manter o local em que um valor é exigido pela sintaxe de idioma quando nenhum valor é necessário ou desejado.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424025"
---
# <a name="unit-type"></a>Tipo unit

O tipo de `unit` é um tipo que indica a ausência de um valor específico; o tipo de `unit` tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.

## <a name="syntax"></a>Sintaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Comentários

Cada F# expressão deve ser avaliada como um valor. Para expressões que não geram um valor de interesse, o valor do tipo `unit` é usado. O tipo de `unit` se assemelha ao tipo de `void` em idiomas C# como C++e.

O tipo de `unit` tem um único valor, e esse valor é indicado pelo token `()`.

O valor do tipo de `unit` geralmente é usado na F# programação para manter o local em que um valor é exigido pela sintaxe da linguagem, mas quando nenhum valor é necessário ou desejado. Um exemplo pode ser o valor de retorno de uma função `printf`. Como as ações importantes da operação de `printf` ocorrem na função, a função não precisa retornar um valor real. Portanto, o valor de retorno é do tipo `unit`.

Algumas construções esperam um valor `unit`. Por exemplo, uma associação de `do` ou qualquer código no nível superior de um módulo deve ser avaliado como um valor de `unit`. O compilador relata um aviso quando um `do` associação ou código no nível superior de um módulo produz um resultado diferente do valor de `unit` que não é usado, como mostrado no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Esse aviso é uma característica da programação funcional; Ele não aparece em outras linguagens de programação do .NET. Em um programa puramente funcional, no qual as funções não têm nenhum efeito colateral, o valor final de retorno é o único resultado de uma chamada de função. Portanto, quando o resultado é ignorado, é um possível erro de programação. Embora F# o não seja uma linguagem de programação puramente funcional, é uma boa prática seguir o estilo de programação funcional sempre que possível.

## <a name="see-also"></a>Consulte também

- [Primitiva](basic-types.md)
- [Referência da Linguagem F#](index.md)
