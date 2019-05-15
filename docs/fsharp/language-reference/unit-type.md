---
title: Tipo unit
description: Saiba como o F# tipo de 'unit' geralmente é usado para manter o lugar onde um valor é exigido pela sintaxe de linguagem quando nenhum valor é necessário ou desejado.
ms.date: 05/16/2016
ms.openlocfilehash: d515e19489bfa7de6f17194fd74176cfa0bcd7c9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645130"
---
# <a name="unit-type"></a>Tipo unit

O `unit` tipo é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.

## <a name="syntax"></a>Sintaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Comentários

Cada F# expressão deve ser avaliada como um valor. Para expressões que não geram um valor que é de interesse, o valor do tipo `unit` é usado. O `unit` tipo é semelhante a `void` tipo em linguagens como c# e C++.

O `unit` tipo tem um único valor, e esse valor é indicado pelo token `()`.

O valor de `unit` tipo geralmente é usado em F# programação para manter o lugar onde um valor é exigido pela sintaxe de linguagem, mas quando nenhum valor é necessário ou desejado. Um exemplo pode ser o valor retornado de uma `printf` função. Porque as ações importantes do `printf` operação ocorrer na função, a função não precisa retornar um valor real. Portanto, o valor retornado é do tipo `unit`.

Algumas construções esperam um `unit` valor. Por exemplo, uma `do` qualquer código no nível superior de um módulo ou a associação deve ser avaliada para um `unit` valor. O compilador relatará um aviso quando um `do` código no nível superior de um módulo ou a associação produz um resultado diferente do `unit` valor não for usado, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Esse aviso é uma característica da programação funcional; ele não aparece em outras linguagens de programação do .NET. Em um programa puramente funcional, em que funções não têm nenhum efeito colateral, o valor de retorno final é o único resultado de uma chamada de função. Portanto, quando o resultado é ignorado, ele é um possível erro de programação. Embora F# não é puramente funcional linguagem de programação, é uma boa prática seguir o estilo de programação funcional, sempre que possível.

## <a name="see-also"></a>Consulte também

- [Primitivos](primitive-types.md)
- [Referência da Linguagem F#](index.md)
