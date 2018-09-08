---
title: Tipo unit (F#)
description: "Saiba como o tipo de 'unidade' F # geralmente é usado para manter o lugar onde um valor é exigido pela sintaxe de linguagem quando nenhum valor é necessário ou desejado."
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204650"
---
# <a name="unit-type"></a>Tipo unit

O `unit` tipo é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.

## <a name="syntax"></a>Sintaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Comentários

Cada expressão F # deve ser avaliada como um valor. Para expressões que não geram um valor que é de interesse, o valor do tipo `unit` é usado. O `unit` tipo é semelhante a `void` tipo em linguagens como c# e C++.

O `unit` tipo tem um único valor, e esse valor é indicado pelo token `()`.

O valor da `unit` tipo geralmente é usado em F # de programação para manter o lugar onde um valor é exigido pela sintaxe de linguagem, mas quando nenhum valor é necessário ou desejado. Um exemplo pode ser o valor retornado de uma `printf` função. Porque as ações importantes do `printf` operação ocorrer na função, a função não precisa retornar um valor real. Portanto, o valor retornado é do tipo `unit`.

Algumas construções esperam um `unit` valor. Por exemplo, uma `do` qualquer código no nível superior de um módulo ou a associação deve ser avaliada para um `unit` valor. O compilador relatará um aviso quando um `do` código no nível superior de um módulo ou a associação produz um resultado diferente do `unit` valor não for usado, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Esse aviso é uma característica da programação funcional; ele não aparece em outras linguagens de programação do .NET. Em um programa puramente funcional, em que funções não têm nenhum efeito colateral, o valor de retorno final é o único resultado de uma chamada de função. Portanto, quando o resultado é ignorado, ele é um possível erro de programação. Embora o F # não é uma linguagem de programação puramente funcional, é uma boa prática seguir o estilo de programação funcional, sempre que possível.

## <a name="see-also"></a>Consulte também

- [Primitivos](primitive-types.md)
- [Referência da Linguagem F#](index.md)
