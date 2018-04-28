---
title: Funções embutidas (F#)
description: 'Saiba como usar o F # embutido funções que são integradas diretamente no código de chamada.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cb0addd1456af1ab97e249b9c5ece4d9f0818fa3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="inline-functions"></a>Funções embutidas

*Funções embutidas* são funções que são integradas diretamente no código de chamada.


## <a name="using-inline-functions"></a>Usando funções embutidas
Quando você usar parâmetros de tipo estático, todas as funções que são parametrizadas por parâmetros de tipo devem ser embutida. Isso garante que o compilador pode resolver esses parâmetros de tipo. Quando você usar parâmetros de tipo genérico comum, não há nenhuma restrição.

Além de habilitar o uso de restrições de membro, funções embutidas podem ser úteis na otimização de código. No entanto, o uso excessivo de funções embutidas pode causar seu código seja menos resistentes a mudanças em otimizações do compilador e a implementação de funções de biblioteca. Por esse motivo, você deve evitar usar funções embutidas para otimização, a menos que você tentou todas as outras técnicas de otimização. Fazer um método ou função em linha pode muitas vezes melhorar desempenho, mas que não é sempre o caso. Portanto, você também deve usar medidas de desempenho para verificar o que fazer qualquer determinada função embutida na verdade tem um efeito positivo.

O `inline` modificador pode ser aplicado às funções de nível superior, no nível de módulo ou no nível de método em uma classe.

O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutido e um método estático em linha.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>Funções embutidas e Inferência de tipo
A presença de `inline` afeta a inferência de tipos. Isso ocorre porque funções embutidas podem ter resolvidos estaticamente parâmetros de tipo, enquanto as funções embutidas não não é possível. O exemplo de código a seguir mostra um caso onde `inline` é útil porque você está usando uma função que tem um parâmetro de tipo resolvidos estaticamente, o `float` operador de conversão.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Sem o `inline` força de inferência de tipo de modificador, a função para usar um tipo específico, nesse caso `int`. Mas com o `inline` modificador, a função também é inferido para ter um parâmetro de tipo resolvidos estaticamente. Com o `inline` modificador, o tipo é inferido para ser o seguinte:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Isso significa que a função aceita qualquer tipo que oferece suporte a uma conversão **float**.


## <a name="see-also"></a>Consulte também
[Funções](index.md)

[Restrições](../generics/constraints.md)

[Parâmetros de Tipo Resolvidos Estaticamente](../generics/statically-resolved-type-parameters.md)
