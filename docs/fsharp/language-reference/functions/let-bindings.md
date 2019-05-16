---
title: Associações let
description: Saiba como usar um F# 'let' associação, que associa um identificador com um valor ou uma função.
ms.date: 05/16/2016
ms.openlocfilehash: ac33ee761cd4881f3d82d6680a07f62a1d7e77e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641882"
---
# <a name="let-bindings"></a>Associações let

Um *associação* associa um identificador com um valor ou uma função. Você usa o `let` palavra-chave para associar um nome para a função ou valor.

## <a name="syntax"></a>Sintaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Comentários

O `let` palavra-chave é usada em expressões para definir valores ou valores de função para um ou mais nomes de associação. A forma mais simples de `let` expressão associa um nome a um valor simple, da seguinte maneira.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Se você separar a expressão do identificador por meio de uma nova linha, você deve recuar cada linha da expressão, como no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Em vez de apenas um nome, um padrão que contém os nomes pode ser especificado, por exemplo, uma tupla, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

O *corpo da expressão* é a expressão na qual os nomes são usados. A expressão do corpo é exibida em sua própria linha, recuada de linha para cima exatamente com o primeiro caractere no `let` palavra-chave:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

Um `let` associação pode aparecer no nível de módulo na definição de um tipo de classe ou em escopos locais, como em uma definição de função. Um `let` vinculação no nível em um módulo ou em um tipo de classe superior não precisa ter um corpo de expressão, mas em outros níveis de escopo, a expressão do corpo é necessário. Os nomes associados serão úteis após o ponto da definição, mas não a qualquer momento antes do `let` associação é exibida, conforme é ilustrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Associações de função

Associações de função seguem as regras para associações de valor, exceto que as associações de função incluem o nome da função e os parâmetros, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Em geral, os parâmetros são padrões, como um padrão de tupla:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

Um `let` expressão de associação é avaliada como o valor da última expressão. Portanto, no exemplo de código, o valor de `result` é computada a partir `100 * function3 (1, 2)`, que é avaliado como `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Para obter mais informações, consulte [Funções](index.md).

## <a name="type-annotations"></a>Anotações de tipo

Você pode especificar tipos de parâmetros, incluindo dois-pontos (:) seguido por um nome de tipo, tudo entre parênteses. Você também pode especificar o tipo do valor de retorno, acrescentando o dois-pontos e o tipo após o último parâmetro. As anotações de tipo completo da `function1`, com números inteiros como os tipos de parâmetro, seria da seguinte maneira.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Quando não houver nenhum parâmetro de tipo explícito, inferência de tipo é usada para determinar os tipos de parâmetros de funções. Isso pode incluir automaticamente generalizar o tipo de um parâmetro para ser genérico.

Para obter mais informações, consulte [generalização automática](../generics/automatic-generalization.md) e [inferência de tipo](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Associações let em classes

Um `let` associação pode aparecer em um tipo de classe, mas não em uma estrutura ou o tipo de registro. Para usar um let de associação em um tipo de classe, a classe deve ter um construtor primário. Parâmetros do construtor devem aparecer após o nome do tipo na definição de classe. Um `let` associação em um tipo de classe define os campos particulares e membros para esse tipo de classe e, em conjunto com `do` associações de tipo, o código para o construtor primário para o tipo de formulários. Os exemplos de código a seguir mostram uma classe `MyClass` com campos privados `field1` e `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Os escopos de `field1` e `field2` são limitados ao tipo no qual eles são declarados. Para obter mais informações, consulte [ `let` associações em Classes](../members/let-bindings-in-classes.md) e [Classes](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Associações let de parâmetros de tipo em

Um `let` vinculação no nível de módulo em um tipo ou em uma expressão de computação pode ter parâmetros de tipo explícito. Um let de associação em uma expressão, como em uma definição de função não pode ter parâmetros de tipo. Para obter mais informações, consulte [Genéricos](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Associações let de atributos em

Atributos podem ser aplicados ao nível superior `let` associações em um módulo, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Escopo e a acessibilidade das associações Let

O escopo de uma entidade declarada com uma associação let é limitado à parte do recipiente de escopo (por exemplo, uma função, módulo, arquivo ou classe) depois que a associação é exibida. Portanto, pode-se dizer que uma associação let introduz um nome em um escopo. Em um módulo, um valor de associação let ou uma função é acessível para clientes de um módulo desde que o módulo está acessível, já que as associações let em um módulo são compiladas em funções públicas do módulo. Por outro lado, as associações let em uma classe são privadas à classe.

Normalmente, as funções em módulos devem ser qualificadas pelo nome do módulo quando usado pelo código do cliente. Por exemplo, se um módulo `Module1` tem uma função `function1`, especificam os usuários `Module1.function1` para referir-se a função.

Os usuários de um módulo podem usar uma declaração de importação para tornar as funções dentro daquele módulo disponíveis para uso sem serem qualificados pelo nome do módulo. No exemplo que acabei de mencionar, os usuários do módulo podem nesse caso, abra o módulo usando a abertura da declaração de importação `Module1` e depois disso, se referir a `function1` diretamente.

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Alguns módulos têm o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), o que significa que as funções que eles expõem devem ser qualificadas com o nome do módulo. Por exemplo, o F# módulo de lista tem esse atributo.

Para obter mais informações sobre módulos e controle de acesso, consulte [módulos](../modules.md) e [controle de acesso](../access-control.md).

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
- [`let`Associações em Classes](../members/let-bindings-in-classes.md)
