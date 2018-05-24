---
title: Métodos (F#)
description: 'Saiba como um método de F # é uma função associada a um tipo que são usadas para expor e implementar a funcionalidade e o comportamento de objetos e tipos.'
ms.date: 05/16/2016
ms.openlocfilehash: e30300b4dd6cc26712a5adbc8abf720f2c312a6f
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="methods"></a>Métodos

Um *método* é uma função que está associada um tipo. Em programação orientada a objeto, os métodos são usados para expor e implementar a funcionalidade e o comportamento de objetos e tipos.


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
Na sintaxe anterior, você pode ver as várias formas de definições e declarações de método. Mais corpos de método, uma quebra de linha segue o sinal de igual (=) e o corpo do método inteiro é recuado.

Atributos podem ser aplicados a qualquer declaração de método. Eles precedem a sintaxe para uma definição de método e geralmente são listados em uma linha separada. Para obter mais informações, consulte [Atributos](../attributes.md).

Métodos podem ser marcados como `inline`. Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).

Métodos embutido não podem ser usado recursivamente dentro do tipo; não é necessário usar explicitamente o `rec` palavra-chave.


## <a name="instance-methods"></a>Métodos de instância
Métodos de instância são declarados com a `member` palavra-chave e uma *identificador Self*, seguido por um ponto (.) e o nome do método e parâmetros. Como é o caso para `let` associações, o *a lista de parâmetros* pode ser um padrão. Normalmente, você coloque método parâmetros entre parênteses na forma de tupla, que é os modo como os métodos são exibidos em F # quando elas são criadas em outras linguagens do .NET Framework. No entanto, o formulário na forma curried (parâmetros separados por espaços) também é comum, e outros padrões têm suporte também.

O exemplo a seguir ilustra a definição e o uso de um método de instância não-abstrato.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Dentro de métodos de instância, não use o identificador de autoatendimento para campos de acesso definidos usando associações let. Use o identificador de autoatendimento ao acessar outros membros e propriedades.


## <a name="static-methods"></a>Métodos estáticos
A palavra-chave `static` é usado para especificar que um método pode ser chamado sem uma instância e não está associado uma instância do objeto. Caso contrário, os métodos são métodos de instância.

O exemplo na próxima seção mostra os campos declarados com o `let` palavra-chave, membros de propriedade declarado com o `member` palavra-chave e um método estático declarado com o `static` palavra-chave.

O exemplo a seguir ilustra a definição e o uso de métodos estáticos. Suponha que essas definições de método em de `SomeType` classe na seção anterior.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Métodos abstratos e virtuais
A palavra-chave `abstract` indica que um método tem um slot de expedição virtual e pode não ter uma definição de classe. Um *slot de expedição virtual* é uma entrada em uma tabela interna de funções que é usada em tempo de execução para procurar a função virtual chamadas em um tipo orientada a objeto. O mecanismo de expedição virtual é o mecanismo que implementa *polimorfismo*, um recurso importante de programação orientada a objeto. É uma classe que tem pelo menos um método abstrato sem uma definição de um *classe abstrata*, que significa que nenhuma instância pode ser criada dessa classe. Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).

Declarações de método abstract não incluir um corpo de método. Em vez disso, o nome do método é seguido por dois-pontos (:) e uma assinatura de tipo para o método. A assinatura de tipo de um método é o mesmo que o mostrado pelo IntelliSense quando você pausa o ponteiro do mouse sobre um nome de método no código Editor do Visual Studio, exceto sem nomes de parâmetro. Assinaturas de tipo também são exibidas pelo interpretador, fsi.exe, quando você estiver trabalhando interativamente. A assinatura de tipo de um método é formada por lista os tipos de parâmetros, seguidos pelo tipo de retorno, com símbolos de separador apropriado. Na forma curried parâmetros são separados por `->` e parâmetros de tupla são separados por `*`. O valor de retorno sempre é separado dos argumentos por um `->` símbolo. Parênteses podem ser usados para agrupar parâmetros complexos, como quando um tipo de função é um parâmetro, ou para indicar quando uma tupla é tratada como um único parâmetro em vez de dois parâmetros.

Você também pode fornecer definições padrão de métodos abstratos adicionando a definição para a classe e usando o `default` palavra-chave, conforme mostrado no bloco de sintaxe neste tópico. Um método abstrato que tenha uma definição na mesma classe é equivalente a um método virtual de outras linguagens do .NET Framework. Se existe ou não uma definição, o `abstract` palavra-chave cria um novo slot de expedição na tabela de função virtual para a classe.

Independentemente de se uma classe base implementa seus métodos abstratos, classes derivadas podem fornecer implementações de métodos abstratos. Para implementar um método abstrato em uma classe derivada, defina um método que tem o mesmo nome e assinatura na classe derivada, exceto o uso de `override` ou `default` palavra-chave e forneça o corpo do método. As palavras-chave `override` e `default` têm exatamente o mesmo significado. Use `override` se o novo método substitui uma implementação da classe base; use `default` quando você cria uma implementação na mesma classe como abstrata declaração original. Não use o `abstract` palavra-chave no método que implementa o método foi declarado abstrato de classe base.

O exemplo a seguir ilustra um método abstrato `Rotate` que tem uma implementação do padrão, o equivalente de um método virtual do .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

O exemplo a seguir ilustra uma classe derivada que substitui um método de classe base. Nesse caso, a substituição altera o comportamento para que o método não fará nada.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Métodos Sobrecarregados
Métodos sobrecarregados são métodos que têm nomes idênticos em um determinado tipo, mas com argumentos diferentes. Em F #, argumentos opcionais são geralmente usados em vez de métodos sobrecarregados. No entanto, os métodos sobrecarregados são permitidos no idioma, desde que os argumentos na forma de tupla, formulário na forma curried não.

## <a name="optional-arguments"></a>Argumentos opcionais

A partir do F # 4.1, você pode ter argumentos opcionais com um valor de parâmetro padrão também nos métodos.  Isso é para ajudar a facilitar a interoperação com código c#.  O exemplo a seguir demonstra a sintaxe:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Observe que o valor passado para `DefaultParameterValue` deve corresponder ao tipo de entrada.  No exemplo acima, é um `int`.  Tentando passar um valor não inteiro em `DefaultParameterValue` resultaria em um erro de compilação.

## <a name="example-properties-and-methods"></a>Exemplo: Propriedades e métodos
O exemplo a seguir contém um tipo que tem exemplos de campos, funções private, propriedades e um método estático.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Consulte também
[Membros](index.md)
