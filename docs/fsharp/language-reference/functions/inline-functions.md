---
title: Funções embutidas (F#)
description: 'Saiba como usar F # embutido funções integradas diretamente ao código de chamada.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875051"
---
# <a name="inline-functions"></a>Funções embutidas

*Funções embutidas* são funções que são integradas diretamente ao código de chamada.

## <a name="using-inline-functions"></a>Usando funções embutidas

Quando você usa os parâmetros de tipo estático, todas as funções que são parametrizadas pelos parâmetros de tipo devem ser embutida. Isso garante que o compilador pode resolver esses parâmetros de tipo. Quando você usa os parâmetros de tipo genérico comum, não há nenhuma restrição.

Além de habilitar o uso de restrições de membro, funções embutidas podem ser útil para otimizar o código. No entanto, uso excessivo de funções embutidas pode fazer com que seu código seja menos resistentes a alterações em otimizações do compilador e a implementação das funções de biblioteca. Por esse motivo, você deve evitar o uso de funções embutidas para a otimização, a menos que você tenha tentado todas as outras técnicas de otimização. Tornar um método ou função embutida, às vezes, pode melhorar desempenho, mas que não é sempre o caso. Portanto, você também deve usar medidas de desempenho para verificar o que fazer qualquer determinada função embutida de fato, tem um efeito positivo.

O `inline` modificador pode ser aplicado a funções de nível superior, no nível de módulo ou no nível de método em uma classe.

O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutidos e um método estático em linha.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Funções embutidas e Inferência de tipo

A presença de `inline` afeta inferência de tipos. Isso é porque as funções embutidas podem resolveram estaticamente os parâmetros de tipo, enquanto funções não embutidas não podem. O exemplo de código a seguir mostra um caso em que `inline` é útil porque você está usando uma função que tem um parâmetro de tipo estaticamente resolvidos, o `float` operador de conversão.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Sem o `inline` modificador, força a inferência de tipo para levar a um tipo específico, nesse caso, a função `int`. Mas com o `inline` modificador, a função também é inferida para ter um parâmetro de tipo estaticamente resolvidos. Com o `inline` modificador, o tipo é inferido para ser o seguinte:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Isso significa que a função aceita qualquer tipo que dá suporte a uma conversão **float**.

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
- [Restrições](../generics/constraints.md)
- [Parâmetros de Tipo Resolvidos Estaticamente](../generics/statically-resolved-type-parameters.md)
