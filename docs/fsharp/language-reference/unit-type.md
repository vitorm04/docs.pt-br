---
title: Tipo unit (F#)
description: "Saiba como o tipo 'unit' F # é geralmente usado para manter o lugar onde um valor é exigido pela sintaxe de linguagem quando nenhum valor é necessário ou desejado."
ms.date: 05/16/2016
ms.openlocfilehash: fdd6b62f9d5c6d73407d5326c7d1f66d55780682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="unit-type"></a>Tipo unit

O `unit` é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.


## <a name="syntax"></a>Sintaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Comentários
Cada expressão F # deve ser avaliada como um valor. Para expressões que não geram um valor que é de interesse, o valor do tipo `unit` é usado. O `unit` tipo é semelhante a `void` tipo em linguagens como c# e C++.

O `unit` tipo tem um único valor, e esse valor é indicada pelo token de `()`.

O valor da `unit` tipo geralmente é usado em F # de programação para manter o lugar onde um valor é exigido pela sintaxe de linguagem, mas quando nenhum valor é necessário ou desejado. Um exemplo pode ser o valor de retorno de uma `printf` função. Como as ações importantes do `printf` operação ocorrer na função, a função não precisa retornar um valor real. Portanto, o valor retornado é do tipo `unit`.

Algumas construções esperam um `unit` valor. Por exemplo, um `do` associação ou qualquer código no nível superior de um módulo deve ser avaliada para um `unit` valor. O compilador relata um aviso quando um `do` associação ou código no nível superior de um módulo produz um resultado diferente de `unit` valor não for usado, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Esse aviso é uma característica de programação funcional; ele não aparece em outras linguagens de programação do .NET. Em um programa totalmente funcional, nos quais funções não têm efeitos colaterais, o valor de retorno final é o único resultado de uma chamada de função. Portanto, quando o resultado é ignorado, ele é um possível erro de programação. Embora o F # não é uma linguagem de programação totalmente funcional, é uma boa prática segue o estilo de programação funcional sempre que possível.

## <a name="see-also"></a>Consulte também
[Primitivos](primitive-types.md)

[Referência da Linguagem F#](index.md)
