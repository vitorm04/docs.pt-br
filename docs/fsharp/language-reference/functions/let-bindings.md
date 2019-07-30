---
title: Associações let
description: Saiba como usar uma F# Associação ' Let ', que associa um identificador a um valor ou função.
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630643"
---
# <a name="let-bindings"></a>Associações let

Uma *Associação* associa um identificador a um valor ou função. Você usa a `let` palavra-chave para associar um nome a um valor ou função.

## <a name="syntax"></a>Sintaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Comentários

A `let` palavra-chave é usada em expressões de associação para definir valores ou valores de função para um ou mais nomes. A forma mais simples da `let` expressão associa um nome a um valor simples, como a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Se você separar a expressão do identificador usando uma nova linha, deverá recuar cada linha da expressão, como no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Em vez de apenas um nome, um padrão que contém nomes pode ser especificado, por exemplo, uma tupla, como mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

A *expressão Body* é a expressão na qual os nomes são usados. A expressão de corpo aparece em sua própria linha, recuada para alinhar exatamente com o primeiro caractere na `let` palavra-chave:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

Uma `let` associação pode aparecer no nível do módulo, na definição de um tipo de classe ou em escopos locais, como em uma definição de função. Uma `let` associação no nível superior em um módulo ou em um tipo de classe não precisa ter uma expressão Body, mas em outros níveis de escopo, a expressão Body é necessária. Os nomes associados são utilizáveis após o ponto de definição, mas não a qualquer momento antes que `let` a associação seja exibida, como é ilustrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Associações de função

As associações de função seguem as regras para associações de valor, exceto que as associações de função incluem o nome da função e os parâmetros, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Em geral, os parâmetros são padrões, como um padrão de tupla:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

Uma `let` expressão de associação é avaliada como o valor da última expressão. Portanto, no exemplo de código a seguir, o valor `result` de é computado de `100 * function3 (1, 2)`, que é `300`avaliado como.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Para obter mais informações, consulte [Funções](index.md).

## <a name="type-annotations"></a>Anotações de tipo

Você pode especificar tipos de parâmetros, incluindo dois-pontos (:) seguido por um nome de tipo, todos incluídos entre parênteses. Você também pode especificar o tipo do valor de retorno acrescentando os dois-pontos e o tipo após o último parâmetro. As anotações de tipo completo para `function1`, com inteiros como os tipos de parâmetro, seriam como a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Quando não há nenhum parâmetro de tipo explícito, a inferência de tipos é usada para determinar os tipos de parâmetros de funções. Isso pode incluir a generalização automática do tipo de um parâmetro como genérico.

Para obter mais informações, consulte [generalização automática](../generics/automatic-generalization.md) e inferência de [tipos](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Associações let em classes

Uma `let` associação pode aparecer em um tipo de classe, mas não em um tipo de estrutura ou de registro. Para usar uma associação let em um tipo de classe, a classe deve ter um construtor principal. Os parâmetros do construtor devem aparecer após o nome do tipo na definição de classe. Uma `let` associação em um tipo de classe define campos privados e membros para esse tipo de classe e, `do` junto com associações no tipo, forma o código para o construtor primário para o tipo. Os exemplos de código a seguir mostram `MyClass` uma classe com `field1` campos `field2`privados e.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Os escopos `field1` de `field2` e são limitados ao tipo no qual são declarados. Para obter mais informações, consulte [ `let` associações em classes](../members/let-bindings-in-classes.md) e [classes](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Parâmetros de tipo em permitir associações

Uma `let` associação no nível do módulo, em um tipo ou em uma expressão de computação pode ter parâmetros de tipo explícitos. Uma associação let em uma expressão, como em uma definição de função, não pode ter parâmetros de tipo. Para obter mais informações, consulte [Genéricos](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atributos em permitir associações

Os atributos podem ser aplicados a associações de `let` nível superior em um módulo, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Escopo e acessibilidade de associações Let

O escopo de uma entidade declarada com uma associação let é limitado à parte do escopo de contenção (como uma função, módulo, arquivo ou classe) depois que a associação é exibida. Portanto, pode ser dito que uma associação let introduz um nome em um escopo. Em um módulo, uma função ou valor de Let é acessível aos clientes de um módulo, desde que o módulo esteja acessível, pois as associações Let em um módulo são compiladas em funções públicas do módulo. Por outro lado, permite que as associações em uma classe sejam privadas para a classe.

Normalmente, as funções em módulos devem ser qualificadas pelo nome do módulo quando usadas pelo código do cliente. Por exemplo, se um módulo `Module1` tiver uma função `function1`, os usuários especificarão `Module1.function1` a referência à função.

Os usuários de um módulo podem usar uma declaração de importação para tornar as funções dentro desse módulo disponíveis para uso sem serem qualificadas pelo nome do módulo. No exemplo que acabamos de mencionar, os usuários do módulo podem, nesse caso, abrir o módulo usando a Declaração `Module1` de importação aberta e `function1` depois se referirem diretamente.

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

Alguns módulos têm o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), o que significa que as funções que eles expões devem ser qualificadas com o nome do módulo. Por exemplo, o F# módulo lista tem esse atributo.

Para obter mais informações sobre módulos e controle de acesso, consulte [módulos](../modules.md) e [controle de acesso](../access-control.md).

## <a name="see-also"></a>Consulte também

- [Funções](index.md)
- [`let`Associações em Classes](../members/let-bindings-in-classes.md)
