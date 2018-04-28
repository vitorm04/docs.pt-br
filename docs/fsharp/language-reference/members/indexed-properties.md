---
title: Propriedades indexadas (F#)
description: 'Saiba mais sobre F # indexada propriedades, que são propriedades que fornecem acesso de matriz aos dados ordenados.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 39396b3a5ec43f9a8ab0df96afeb69e05801c752
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="indexed-properties"></a>Propriedades indexadas

*Propriedades indexadas* são ordenadas de propriedades que fornecem acesso de matriz aos dados.


## <a name="syntax"></a>Sintaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Comentários
Três formas de sintaxe anterior mostram como definir propriedades indexadas que têm ambos um `get` e um `set` método, ter um `get` método apenas, ou ter um `set` método apenas. Você também pode combinar as duas opções a sintaxe mostrada para somente get e a sintaxe mostrada apenas o conjunto de e produzir uma propriedade que tem get e set. Este último formulário permite que você coloque modificadores de acessibilidade diferentes e os atributos em get e definir métodos.

Quando o *PropertyName* é `Item`, o compilador trata a propriedade como uma propriedade indexada padrão. Um *propriedade default indexada* é uma propriedade que você pode acessar usando a sintaxe de matriz na instância do objeto. Por exemplo, se `obj` é um objeto do tipo que define essa propriedade, a sintaxe `obj.[index]` é usada para acessar a propriedade.

A sintaxe para acessar uma propriedade indexada de não-padrão é fornecer o nome da propriedade e o índice entre parênteses. Por exemplo, se a propriedade é `Ordinal`, você escreve `obj.Ordinal(index)` para acessá-lo.

Independentemente de qual formato você usar, você sempre deve usar o formulário na forma curried para o `set` método em uma propriedade indexada. Para obter informações sobre as funções na forma curried, consulte [funções](../functions/index.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra a definição e o uso do padrão e não padrão propriedades indexadas que obter e definir métodos.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Saída

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Propriedades indexadas com diversas variáveis de índice
Propriedades indexadas podem ter mais de uma variável de índice. Nesse caso, as variáveis são separadas por vírgulas, quando a propriedade é usada. O método set em uma propriedade deve ter dois argumentos na forma curried, o primeiro deles é uma tupla que contém as chaves, e o segundo é o valor que está sendo definido.

O código a seguir demonstra o uso de uma propriedade indexada com diversas variáveis de índice.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>Consulte também
[Membros](index.md)
