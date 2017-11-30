---
title: Registros (F#)
description: "Saiba como registros de F # representam agregações simples de valores nomeados, opcionalmente com membros."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: f5ade1db39431d99f10eb6967f02335123b83d34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="records"></a>Registros

Registros representam agregações simples de valores nomeados, opcionalmente com membros.  A partir do F # 4.1, eles podem ser tipos de estruturas ou referência.  Eles são tipos de referência por padrão.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, *typename* é o nome do tipo de registro *label1* e *label2* são nomes de valores, conhecidos como *rótulos*, e *type1* e *type2* são os tipos desses valores. *lista de membros* é a lista opcional de membros para o tipo.  Você pode usar o `[<Struct>]` atributo para criar um registro de struct, em vez de um registro que é um tipo de referência.

A seguir estão alguns exemplos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

Quando cada rótulo em uma linha separada, o ponto e vírgula é opcional.

Você pode definir valores em expressões, conhecidas como *gravar expressões*. O compilador infere o tipo dos rótulos usada (se os rótulos são suficientemente diferentes daquelas de outros tipos de registro). Chaves ({}) coloque a expressão de registro. O código a seguir mostra uma expressão de registro que inicia um registro com três elementos de float com rótulos `x`, `y` e `z`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

Não use a forma abreviada se pode haver outro tipo que também tem os mesmos rótulos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

Os rótulos do tipo declarado mais recentemente têm precedência sobre as do tipo declarado anteriormente, portanto, no exemplo anterior, `mypoint3D` é inferido para ser `Point3D`. Você pode especificar explicitamente o tipo de registro, como no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

Métodos podem ser definidos para os tipos de registro como tipos de classe.

## <a name="creating-records-by-using-record-expressions"></a>Criar registros usando expressões de registro
Você pode inicializar registros usando os rótulos que são definidos no registro. Uma expressão que faz isso é conhecida como um *registro expressão*. Use chaves para colocar a expressão de registro e usar o ponto e vírgula como delimitador.

O exemplo a seguir mostra como criar um registro.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

A ponto e vírgula após o último campo na expressão do registro e na definição de tipo é opcional, independentemente se os campos estão todas em uma linha.

Quando você cria um registro, você deve fornecer valores para cada campo. Você não pode consultar os valores dos outros campos na expressão de inicialização para qualquer campo.

No código a seguir, o tipo de `myRecord2` é inferido dos nomes dos campos. Opcionalmente, você pode especificar o nome do tipo explicitamente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Outra forma de construção de registro pode ser útil quando você precisa copiar um registro existente e possivelmente alterar alguns dos valores de campo. A linha de código a seguir ilustra isso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

Essa forma de expressão de registro é chamada de *copiar e atualizar registro expressão*.

Registros são imutáveis por padrão. No entanto, você pode criar facilmente os registros modificados usando uma expressão de copiar e atualizar. Você também pode especificar explicitamente um campo mutável.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

Não use o atributo DefaultValue com campos de registro. Uma abordagem melhor é definir instâncias padrão dos registros com campos que são inicializados com valores padrão e, em seguida, usar uma cópia e atualizar o registro de expressão para definir todos os campos que são diferentes dos valores padrão.

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>Correspondência de padrão com registros
Registros podem ser usados com a correspondência de padrões. Você pode especificar explicitamente o alguns campos e fornecer variáveis para outros campos que serão atribuídos quando ocorre uma correspondência. O exemplo de código a seguir ilustra isso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

A saída desse código é da seguinte maneira.

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>Diferenças entre Classes e registros
Campos de registro diferem das classes automaticamente, eles são expostos como propriedades, e são usadas na criação e cópia de registros. Construção de registro também é diferente da construção de classe. Em um tipo de registro, você não pode definir um construtor. Em vez disso, a sintaxe de construção descrita neste tópico se aplica. Classes não têm nenhuma relação direta entre os parâmetros do construtor, campos e propriedades.

Como tipos de união e estrutura de registros tem semântica de igualdade estrutural. As classes têm referência semântica de igualdade. O exemplo de código a seguir demonstra isso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

Se você escrever o mesmo código com classes, os objetos de dois classe seria diferentes porque os dois valores representa dois objetos no heap e somente os endereços seriam comparados (a menos que o tipo de classe substitui o `System.Object.Equals` método).

Se precisar fazer referência a igualdade de registros, adicione o atributo `[<ReferenceEquality>]` acima do registro.

## <a name="see-also"></a>Consulte também
[Tipos F#](fsharp-types.md)

[Classes](classes.md)

[Referência da Linguagem F#](index.md)

[Igualdade de referência](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[Correspondência Padrão](pattern-matching.md)
