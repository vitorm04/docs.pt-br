---
title: Enumerações (F#)
description: 'Saiba como usar o F # enumerações em vez de literais para tornar o código mais legível e sustentável.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4b1a61fb69403f826733893667e55991d39867c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="enumerations"></a>Enumerações

*Enumerações*, também conhecido como *enums*, são tipos integrais onde os rótulos são atribuídos a um subconjunto dos valores. Você pode usá-los no lugar de literais para tornar o código mais legível e fácil de manter.


## <a name="syntax"></a>Sintaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Comentários
Uma enumeração parece muito, como uma união discriminada que tenha valores simples, exceto que os valores podem ser especificados. Normalmente, os valores são inteiros que começam em 0 ou 1 ou números inteiros que representam as posições de bit. Se uma enumeração destina-se para representar as posições de bit, você também deve usar o [sinalizadores](xref:System.FlagsAttribute) atributo.

O tipo subjacente da enumeração é determinado de literal que é usada, para que, por exemplo, você pode usar literais com um sufixo, como `1u`, `2u`, e assim por diante, para um inteiro sem sinal (`uint32`) tipo.

Quando você faz referência os valores nomeados, você deve usar o nome do tipo de enumeração em si como um qualificador, ou seja, `enum-name.value1`, não apenas `value1`. Esse comportamento é diferente do uniões discriminadas. Isso ocorre porque enumerações sempre têm a [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atributo.

O código a seguir mostra a declaração e o uso de uma enumeração.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Você pode converter facilmente enumerações para o tipo subjacente usando o operador apropriado, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Tipos enumerados podem ter um dos seguintes tipos de base: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, e `char`. Tipos de enumeração são representados no .NET Framework, como tipos que são herdados de `System.Enum`, que por sua vez é herdado do `System.ValueType`. Portanto, são tipos de valor que estão localizados na pilha ou embutido no objeto que contém, e qualquer valor do tipo subjacente é um valor válido da enumeração. Isso é significativo quando os valores padrão de correspondência na enumeração, porque você precisa fornecer um padrão que captura os valores sem nome.

O `enum` função na biblioteca F # pode ser usada para gerar um valor de enumeração, até mesmo um valor diferente de predefinida, valores nomeados. Você usa o `enum` funciona da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

O padrão `enum` função funciona com o tipo `int32`. Portanto, não pode ser usado com tipos de enumeração que têm outros tipos de base. Em vez disso, use o seguinte.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Conversões Cast e conversões](casting-and-conversions.md)
