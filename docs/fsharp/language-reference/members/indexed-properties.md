---
title: Propriedades indexadas
description: Saiba mais sobre propriedades indexadas no F#, que permitem o acesso do tipo matriz a dados ordenados.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627564"
---
# <a name="indexed-properties"></a>Propriedades indexadas

Ao definir uma classe que abstrai os dados ordenados, às vezes pode ser útil fornecer acesso indexado a esses dados sem expor a implementação subjacente. Isso é feito com o `Item` membro.

## <a name="syntax"></a>Sintaxe

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Comentários

Os formulários da sintaxe anterior mostram como `get` definir propriedades indexadas que têm um e um `set` método, só têm um `get` método ou só têm um `set` método. Você também pode combinar a sintaxe mostrada somente para get e a sintaxe mostrada somente para Set e produzir uma propriedade que tenha Get e Set. Este último formulário permite que você coloque atributos e modificadores de acessibilidade diferentes nos métodos get e Set.

Usando o nome `Item`, o compilador trata a propriedade como uma propriedade indexada padrão. Uma *propriedade indexada padrão* é uma propriedade que você pode acessar usando a sintaxe do tipo matriz na instância do objeto. Por exemplo, se `o` for um objeto do tipo que define essa propriedade, a sintaxe `o.[index]` será usada para acessar a propriedade.

A sintaxe para acessar uma propriedade indexada não padrão é fornecer o nome da propriedade e o índice entre parênteses, assim como um membro regular. Por exemplo, se a propriedade on `o` for chamada `Ordinal`, você escreverá `o.Ordinal(index)` para acessá-la.

Independentemente do formulário usado, você sempre deve usar o formulário na forma curried para o método set em uma propriedade indexada. Para obter informações sobre as funções do na forma curried, consulte [funções](../functions/index.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra a definição e o uso de propriedades indexadas padrão e não padrão que têm métodos get e Set.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Saída

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Propriedades indexadas com vários valores de índice

As propriedades indexadas podem ter mais de um valor de índice. Nesse caso, os valores são separados por vírgulas quando a propriedade é usada. O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor a ser definido.

O código a seguir demonstra o uso de uma propriedade indexada com vários valores de índice.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
