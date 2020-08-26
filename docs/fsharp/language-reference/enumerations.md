---
title: Enumerações
description: 'Saiba como usar enumerações F # em vez de literais para tornar seu código mais legível e passível de manutenção.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812101"
---
# <a name="enumerations"></a>Enumerações

*Enumerações*, também conhecidas como *enums*, são tipos integrais em que os rótulos são atribuídos a um subconjunto dos valores. Você pode usá-los no lugar de literais para tornar o código mais legível e fácil de manter.

## <a name="syntax"></a>Sintaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Comentários

Uma enumeração é muito parecida com uma união discriminada que tem valores simples, exceto que os valores podem ser especificados. Os valores normalmente são inteiros que começam com 0 ou 1, ou inteiros que representam posições de bits. Se uma enumeração for destinada a representar posições de bits, você também deverá usar o atributo [flags](xref:System.FlagsAttribute) .

O tipo subjacente da enumeração é determinado a partir do literal que é usado, de modo que, por exemplo, você possa usar literais com um sufixo, como `1u` , `2u` e assim por diante, para um tipo inteiro não assinado ( `uint32` ).

Quando você se referir aos valores nomeados, deverá usar o nome do tipo de enumeração como um qualificador, ou seja, `enum-name.value1` , não apenas `value1` . Esse comportamento é diferente do de uniões discriminadas. Isso ocorre porque as enumerações sempre têm o atributo [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) .

O código a seguir mostra a declaração e o uso de uma enumeração.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Você pode facilmente converter enumerações para o tipo subjacente usando o operador apropriado, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Os tipos enumerados podem ter um dos seguintes tipos subjacentes:,,,,,,,, `sbyte` `byte` `int16` `uint16` `int32` `uint32` `int64` `uint16` `uint64` e `char` . Os tipos de enumeração são representados no .NET Framework como tipos herdados de `System.Enum` , que, por sua vez, são herdados de `System.ValueType` . Portanto, eles são tipos de valor que estão localizados na pilha ou embutidos no objeto contentor, e qualquer valor do tipo subjacente é um valor válido da enumeração. Isso é significativo quando o padrão corresponde aos valores de enumeração, pois você precisa fornecer um padrão que captura os valores sem nome.

A `enum` função na biblioteca F # pode ser usada para gerar um valor de enumeração, mesmo um valor diferente de um dos valores nomeados predefinidos. Você usa a `enum` função da seguinte maneira.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

A `enum` função padrão funciona com o tipo `int32` . Portanto, ele não pode ser usado com tipos de enumeração que têm outros tipos subjacentes. Em vez disso, use o seguinte.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Além disso, os casos de enums são sempre emitidos como `public` . Isso é para que eles se alinhem com C# e o restante da plataforma .NET.

## <a name="see-also"></a>Confira também

- [Referência de linguagem F #](index.md)
- [Conversões cast e conversões](casting-and-conversions.md)
