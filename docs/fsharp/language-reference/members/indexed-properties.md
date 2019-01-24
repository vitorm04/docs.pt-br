---
title: Propriedades indexadas
description: Saiba mais sobre as propriedades indexadas no F#, que permitem acesso de matriz aos dados ordenados.
ms.date: 10/17/2018
ms.openlocfilehash: a092da753acacf80807d145051a719df2d3e1520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550962"
---
# <a name="indexed-properties"></a>Propriedades indexadas

Ao definir uma classe que abstrai sobre dados ordenados, às vezes, pode ser útil fornecer acesso indexado para dados sem expor a implementação subjacente. Isso é feito com o `Index` membro.

## <a name="syntax"></a>Sintaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a>Comentários

As formas de sintaxe anterior mostram como definir as propriedades indexadas com as duas uma `get` e uma `set` método, ter um `get` somente, no método ou tem um `set` somente no método. Você também pode combinar dois a sintaxe mostrada para somente get e a sintaxe mostrada para apenas o conjunto e produzir uma propriedade que tem get e set. Este último formulário permite que você coloque os modificadores de acessibilidade diferente e atributos em get e métodos definidos.

Usando o nome `Item`, o compilador trata a propriedade como uma propriedade indexada padrão. Um *propriedade default indexada* é uma propriedade que você pode acessar usando a sintaxe de matriz na instância do objeto. Por exemplo, se `o` é um objeto do tipo que define essa propriedade, a sintaxe `o.[index]` é usado para acessar a propriedade.

A sintaxe para acessar uma propriedade indexada de não-padrão é fornecer o nome da propriedade e o índice entre parênteses, assim como um membro regular. Por exemplo, se a propriedade em `o` é chamado `Ordinal`, você escreve `o.Ordinal(index)` para acessá-lo.

Independentemente de qual formulário usar, você sempre deve usar o formulário na forma curried para o método set em uma propriedade indexada. Para obter informações sobre funções via currying, consulte [funções](../functions/index.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra a definição e uso do padrão e propriedades indexadas de não-padrão obter e definir métodos.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Saída

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a>Propriedades indexadas com vários valores de índice

Propriedades indexadas podem ter mais de um valor de índice. Nesse caso, os valores são separados por vírgulas quando a propriedade é usada. O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor a ser definido.

O código a seguir demonstra o uso de uma propriedade indexada com vários valores de índice.

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix basedon a dictionary
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
