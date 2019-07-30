---
title: Funções embutidas
description: Saiba como usar F# funções embutidas que são integradas diretamente no código de chamada.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630683"
---
# <a name="inline-functions"></a>Funções embutidas

*Funções embutidas* são funções integradas diretamente no código de chamada.

## <a name="using-inline-functions"></a>Usando funções embutidas

Quando você usa parâmetros de tipo estático, todas as funções parametrizadas por parâmetros de tipo devem ser embutidas. Isso garante que o compilador possa resolver esses parâmetros de tipo. Quando você usa parâmetros de tipo genérico comuns, não há essa restrição.

Além de habilitar o uso de restrições de membro, as funções embutidas podem ser úteis para otimizar o código. No entanto, o uso excessivo de funções embutidas pode fazer com que seu código seja menos resistente a alterações em otimizações de compilador e a implementação de funções de biblioteca. Por esse motivo, evite usar funções embutidas para otimização, a menos que você tenha tentado todas as outras técnicas de otimização. Tornar uma função ou método embutido pode, às vezes, melhorar o desempenho, mas esse nem sempre é o caso. Portanto, você também deve usar medidas de desempenho para verificar se a criação de qualquer função embutida na verdade tem um efeito positivo.

O `inline` modificador pode ser aplicado a funções no nível superior, no nível do módulo ou no nível do método em uma classe.

O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutida e um método estático embutido.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Funções embutidas e inferência de tipos

A presença de `inline` afeta a inferência de tipos. Isso ocorre porque as funções embutidas podem ter parâmetros de tipo estaticamente resolvidos, enquanto funções não embutidas não podem. O exemplo de código a seguir mostra um `inline` caso em que é útil porque você está usando uma função que tem um parâmetro de tipo resolvido `float` estaticamente, o operador de conversão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Sem o `inline` modificador, a inferência de tipos força a função a usar um tipo específico `int`, nesse caso. Mas com o `inline` modificador, a função também é inferida para ter um parâmetro de tipo estaticamente resolvido. Com o `inline` modificador, o tipo é inferido para ser o seguinte:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Isso significa que a função aceita qualquer tipo que ofereça suporte a uma conversão para **float**.

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
- [Restrições](../generics/constraints.md)
- [Parâmetros de Tipo Resolvidos Estaticamente](../generics/statically-resolved-type-parameters.md)
