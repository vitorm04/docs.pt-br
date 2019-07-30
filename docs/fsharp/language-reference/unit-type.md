---
title: Tipo unit
description: Saiba como o F# tipo de "unidade" geralmente é usado para manter o local em que um valor é exigido pela sintaxe de idioma quando nenhum valor é necessário ou desejado.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630167"
---
# <a name="unit-type"></a>Tipo unit

O `unit` tipo é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.

## <a name="syntax"></a>Sintaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Comentários

Cada F# expressão deve ser avaliada como um valor. Para expressões que não geram um valor de interesse, o valor do tipo `unit` é usado. O `unit` tipo é semelhante ao `void` tipo em idiomas como C# e C++.

O `unit` tipo tem um único valor e esse valor é indicado pelo token `()`.

O valor do `unit` tipo é geralmente usado na F# programação para manter o local em que um valor é exigido pela sintaxe da linguagem, mas quando nenhum valor é necessário ou desejado. Um exemplo pode ser o valor de retorno de `printf` uma função. Como as ações importantes da `printf` operação ocorrem na função, a função não precisa retornar um valor real. Portanto, o valor de retorno é do `unit`tipo.

Algumas construções esperam um `unit` valor. Por exemplo, uma `do` associação ou qualquer código no nível superior de um módulo deve ser avaliado como um `unit` valor. O compilador relata um aviso quando uma `do` associação ou código no nível superior de um módulo produz um resultado diferente do `unit` valor que não é usado, como mostrado no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Esse aviso é uma característica da programação funcional; Ele não aparece em outras linguagens de programação do .NET. Em um programa puramente funcional, no qual as funções não têm nenhum efeito colateral, o valor final de retorno é o único resultado de uma chamada de função. Portanto, quando o resultado é ignorado, é um possível erro de programação. Embora F# o não seja uma linguagem de programação puramente funcional, é uma boa prática seguir o estilo de programação funcional sempre que possível.

## <a name="see-also"></a>Consulte também

- [Primitiva](primitive-types.md)
- [Referência da Linguagem F#](index.md)
