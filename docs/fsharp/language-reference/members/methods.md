---
title: Métodos
description: Saiba como um método F# é uma função associada a um tipo que é usado para expor e implementar a funcionalidade e o comportamento de objetos e tipos.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400207"
---
# <a name="methods"></a>Métodos

Um *método* é uma função que está associada a um tipo. Na programação orientada a objetos, os métodos são usados para expor e implementar a funcionalidade e o comportamento de objetos e tipos.

## <a name="syntax"></a>Sintaxe

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, você pode ver as várias formas de declarações e definições do método. Em corpos de método mais longos, uma quebra de linha segue o sinal igual (=), e todo o corpo do método é recuado.

Atributos podem ser aplicados a qualquer declaração de método. Eles precedem a sintaxe para uma definição de método e são geralmente listados em uma linha separada. Para obter mais informações, consulte [Atributos](../attributes.md).

Os métodos `inline`podem ser marcados . Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).

Métodos não inline podem ser usados recursivamente dentro do tipo; não há necessidade de usar `rec` explicitamente a palavra-chave.

## <a name="instance-methods"></a>Métodos de ocorrência

Os métodos de instância `member` são declarados com a palavra-chave e um *auto-identificador,* seguidos por um período (.) e o nome e parâmetros do método. Como é o `let` caso das vinculações, a *lista de parâmetros* pode ser um padrão. Normalmente, você inclui parâmetros de método entre parênteses em uma forma tupla, que é a forma como os métodos aparecem em F# quando eles são criados em outras línguas .NET Framework. No entanto, a forma curricular (parâmetros separados por espaços) também é comum, e outros padrões também são suportados.

O exemplo a seguir ilustra a definição e o uso de um método de instância não abstrata.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Dentro dos métodos de instância, não use o autoidentificador para acessar campos definidos usando vinculações de let. Use o autoidentificador ao acessar outros membros e propriedades.

## <a name="static-methods"></a>Métodos estáticos

A palavra-chave `static` é usada para especificar que um método pode ser chamado sem uma instância e não está associado a uma instância de objeto. Caso contrário, os métodos são métodos de ocorrência.

O exemplo na próxima seção mostra `let` campos declarados com a `member` palavra-chave, membros da propriedade `static` declarados com a palavra-chave e um método estático declarado com a palavra-chave.

O exemplo a seguir ilustra a definição e o uso de métodos estáticos. Suponha que essas definições de método estejam na `SomeType` classe na seção anterior.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Métodos abstratos e virtuais

A palavra-chave `abstract` indica que um método tem um slot de despacho virtual e pode não ter uma definição na classe. Um *slot de despacho virtual* é uma entrada em uma tabela de funções mantida internamente que é usada em tempo de execução para procurar chamadas de função virtual em um tipo orientado a objetos. O mecanismo de despacho virtual é o mecanismo que implementa *o polimorfismo,* uma característica importante da programação orientada a objetos. Uma classe que tem pelo menos um método abstrato sem uma definição é uma *classe abstrata,* o que significa que nenhuma instância pode ser criada dessa classe. Para obter mais informações sobre classes abstratas, consulte [Classes Abstratas](../abstract-classes.md).

As declarações de método saabs não incluem um corpo de método. Em vez disso, o nome do método é seguido por um cólon (:) e uma assinatura de tipo para o método. A assinatura do tipo de um método é a mesma mostrada pelo IntelliSense quando você pausa o ponteiro do mouse sobre um nome de método no Visual Studio Code Editor, exceto sem nomes de parâmetros. Assinaturas de tipo também são exibidas pelo intérprete, fsi.exe, quando você está trabalhando de forma interativa. A assinatura do tipo de um método é formada por listar os tipos dos parâmetros, seguido pelo tipo de retorno, com símbolos separadores apropriados. Os parâmetros curried `->` são separados por e `*`os parâmetros tuplos são separados por . O valor de retorno é sempre separado `->` dos argumentos por um símbolo. Parênteses podem ser usados para agrupar parâmetros complexos, como quando um tipo de função é um parâmetro, ou para indicar quando uma tupla é tratada como um único parâmetro, em vez de como dois parâmetros.

Você também pode dar definições padrão de métodos abstratos adicionando a definição à classe e usando a `default` palavra-chave, como mostrado no bloco de sintaxe neste tópico. Um método abstrato que tenha uma definição na mesma classe é equivalente a um método virtual em outras línguas .NET Framework. Se existe ou não `abstract` uma definição, a palavra-chave cria um novo slot de despacho na tabela de funções virtuais para a classe.

Independentemente de uma classe base implementar seus métodos abstratos, as classes derivadas podem fornecer implementações de métodos abstratos. Para implementar um método abstrato em uma classe derivada, defina um método que `override` `default` tenha o mesmo nome e assinatura na classe derivada, exceto usar a palavra-chave, e fornecer o corpo do método. As palavras-chave `override` significam `default` exatamente a mesma coisa. Use `override` se o novo método anular uma implementação de classe base; usar `default` quando você criar uma implementação na mesma classe que a declaração abstrata original. Não use `abstract` a palavra-chave no método que implementa o método que foi declarado abstrato na classe base.

O exemplo a seguir `Rotate` ilustra um método abstrato que tem uma implementação padrão, o equivalente a um método virtual .NET Framework.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

O exemplo a seguir ilustra uma classe derivada que substitui um método de classe base. Neste caso, a substituição muda o comportamento para que o método não faça nada.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Métodos Sobrecarregados

Métodos sobrecarregados são métodos que têm nomes idênticos em um determinado tipo, mas que têm argumentos diferentes. Em F#, argumentos opcionais são geralmente usados em vez de métodos sobrecarregados. No entanto, métodos sobrecarregados são permitidos na língua, desde que os argumentos estejam em forma tuplo, não em forma curricular.

## <a name="optional-arguments"></a>Argumentos opcionais

Começando com F # 4.1, você também pode ter argumentos opcionais com um valor de parâmetro padrão nos métodos.  Isto é para facilitar a interoperação com o código C#.  O exemplo a seguir demonstra a sintaxe:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Observe que o valor `DefaultParameterValue` passado deve corresponder ao tipo de entrada.  Na amostra acima, é `int`um .  Tentar passar um valor não inteiro `DefaultParameterValue` resultaria em um erro de compilação.

## <a name="example-properties-and-methods"></a>Exemplo: Propriedades e Métodos

O exemplo a seguir contém um tipo que tem exemplos de campos, funções privadas, propriedades e um método estático.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Confira também

- [Membros](index.md)
