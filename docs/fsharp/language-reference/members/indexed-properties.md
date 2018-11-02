---
title: Propriedades indexadas (F#)
description: Saiba mais sobre as propriedades indexadas no F#, que permitem acesso de matriz aos dados ordenados.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "49452242"
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

## <a name="indexed-properties-with-multiple-index-variables"></a>Propriedades indexadas com diversas variáveis de índice

Propriedades indexadas podem ter mais de uma variável de índice. Nesse caso, as variáveis são separadas por vírgulas quando a propriedade é usada. O método set em tal propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves e o segundo é o valor que está sendo definido.

O código a seguir demonstra o uso de uma propriedade indexada com diversas variáveis de índice.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
