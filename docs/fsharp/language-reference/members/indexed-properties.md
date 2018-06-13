---
title: Propriedades indexadas (F#)
description: 'Saiba mais sobre F # indexada propriedades, que são propriedades que fornecem acesso de matriz aos dados ordenados.'
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235935"
---
# <a name="indexed-properties"></a>Propriedades indexadas

*Propriedades indexadas* são ordenadas de propriedades que fornecem acesso de matriz aos dados. Eles vêm em três formas:

* `Item`
* `Ordinal`
* `Cardinal`

Um membro de F # deve ser nomeado um desses três nomes para fornecer acesso de matriz. `IndexerName` é usado para representar qualquer uma das três opções abaixo:


## <a name="syntax"></a>Sintaxe

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Comentários
Os formulários de sintaxe anterior mostram como definir propriedades indexadas que têm ambos um `get` e um `set` método, ter um `get` método apenas, ou tem um `set` método apenas. Você também pode combinar as duas opções a sintaxe mostrada para somente get e a sintaxe mostrada apenas o conjunto de e produzir uma propriedade que tem get e set. Este último formulário permite que você coloque modificadores de acessibilidade diferentes e os atributos em get e definir métodos.

Quando o *IndexerName* é `Item`, o compilador trata a propriedade como uma propriedade indexada padrão. Um *propriedade default indexada* é uma propriedade que você pode acessar usando a sintaxe de matriz na instância do objeto. Por exemplo, se `obj` é um objeto do tipo que define essa propriedade, a sintaxe `obj.[index]` é usada para acessar a propriedade.

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
