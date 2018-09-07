---
title: Genéricos (F#)
description: 'Saiba como usar as funções genéricas do F # e tipos que permitem que você escreva código que funciona com uma variedade de tipos sem repetir o código.'
ms.date: 05/16/2016
ms.openlocfilehash: fc061f19c6c7fa737f7ca05aae83fd42c0010b37
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876126"
---
# <a name="generics"></a>Genéricos

Os valores, os métodos, as propriedades e os tipos de agregação, como classes, registros e uniões discriminadas, da função em F# podem ser *genéricos*. As construções genéricas contêm pelo menos um parâmetro de tipo, que é geralmente fornecido pelo usuário da construção genérica. Os tipos e as funções genéricas permitem que você escreva códigos que funcionam com diversos tipos sem repetir o código de cada tipo. Tornar seu código genérico pode ser algo simples em F#, pois normalmente seu código é implicitamente inferido como genérico pelos mecanismos de generalização automática e de inferência de tipos do compilador.

## <a name="syntax"></a>Sintaxe

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>Comentários

A declaração de um tipo ou de uma função explicitamente genérica é muito semelhante a de um tipo ou função não genérica, exceto com relação à especificação (e uso) dos parâmetros de tipo, entre colchetes após o nome da função ou do tipo.

Geralmente, as declarações são implicitamente genéricas. Se você não especificar completamente o tipo de cada parâmetro usado para compor uma função ou tipo, o compilador tentará inferir o tipo de cada parâmetro, o valor e a variável de código que você escreve. Para saber mais, veja [Inferência de tipo](../type-inference.md). Se o código do tipo ou função não restringir de outro modo os tipos de parâmetros, a função ou o tipo será implicitamente genérico. Esse processo é chamado de *generalização automática*. Há alguns limites para a generalização automática. Por exemplo, se o compilador em F# não puder inferir os tipos de uma construção genérica, o compilador relatará um erro que faz referência a uma restrição chamada de *restrição de valor*. Nesse caso, talvez seja necessário adicionar algumas anotações de tipo. Para saber mais sobre generalização automática e restrição de valor e como alterar seu código para resolver esse problema, veja [Generalização automática](automatic-generalization.md).

Na sintaxe anterior, *type-parameters* é uma lista separada por vírgulas de parâmetros que representam tipos desconhecidos, cada um deles começa com uma aspa simples e, opcionalmente, com uma cláusula de restrição que limita ainda mais os tipos que podem ser usados para esse parâmetro de tipo. Para obter a sintaxe das cláusulas de restrição de vários tipos e outras informações sobre restrições, veja [Restrições](constraints.md).

Na sintaxe, *type-definition* é igual à definição de tipo para um tipo não genérico. Ele inclui os parâmetros do construtor para um tipo de classe, uma cláusula `as` opcional, o símbolo de igual, os campos de registro, a cláusula `inherit`, as opções de uma união discriminada, associações `let` e `do`, definições de membro e qualquer outra coisa permitida em uma definição de tipo não genérico.

Os outros elementos de sintaxe são os mesmos para tipos e funções não genéricos. Por exemplo, *object-identifier* é um identificador que representa o objeto contido em si.

Os construtores, os campos e as propriedades não podem ser mais genéricos do que o tipo delimitador. Além disso, os valores em um módulo não podem ser genéricos.

## <a name="implicitly-generic-constructs"></a>Construções implicitamente genéricas

Quando o compilador de F# infere os tipos em seu código, ele trata automaticamente qualquer função que possa ser genérica como genérica. Se você especificar um tipo explicitamente, como um tipo de parâmetro, você evita a generalização automática.

No exemplo de código a seguir, `makeList` é genérico, mesmo que ele ou seus parâmetros não sejam explicitamente declarados como genéricos.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

A assinatura da função é inferida como `'a -> 'a -> 'a list`. Observe que, neste exemplo, `a` e `b` são inferidos com tendo o mesmo tipo. Isso ocorre porque eles são incluídos em uma lista juntos, e todos os elementos de uma lista devem ser do mesmo tipo.

Você também pode tornar uma função genérica usando a sintaxe de aspas simples em uma anotação de tipo para indicar que um tipo de parâmetro é um parâmetro de tipo genérico. No código a seguir, `function1` é genérico porque os parâmetros são declarados dessa maneira, como parâmetros de tipo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Construções explicitamente genéricas

Você também pode tornar uma função genérica declarando explicitamente seus parâmetros de tipo entre colchetes angulares (`<type-parameter>`). O código a seguir ilustra isso.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Como usar construções genéricas

Quando você usa métodos ou funções genéricas, talvez não seja necessário especificar os argumentos de tipo. O compilador usa a inferência de tipo para inferir os argumentos de tipo apropriados. Se ainda houver ambiguidade, forneça argumentos de tipo entre colchetes angulares, separando vários argumentos de tipo por vírgulas.

O código a seguir mostra o uso das funções definidas nas seções anteriores.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

>[!NOTE]
Há duas maneiras de se referir a um tipo genérico por nome. Por exemplo, `list<int>` e `int list` são duas maneiras de se referir a um tipo genérico `list` que tem um único argumento de tipo `int`. A segunda forma é usada apenas com tipos internos de F#, como `list` e `option`. Se houver vários argumentos de tipo, você normalmente usará a sintaxe `Dictionary<int, string>`, mas também é possível usar a sintaxe `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Caracteres curinga como argumentos de tipo

Para especificar se um argumento de tipo deve ser deduzido pelo compilador, você pode usar o sublinhado, ou um símbolo de caractere curinga (`_`), em vez de um argumento de tipo nomeado. Isso será mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Restrições em funções e tipos genéricos

Em uma definição de função ou tipo genérico, você pode usar somente as construções sabidamente disponíveis no parâmetro de tipo genérico. Isso é necessário para habilitar a verificação de chamadas de função e de método no tempo de compilação. Se você declarar explicitamente os parâmetros de tipo, aplique uma restrição explícita a um parâmetro de tipo genérico a fim de notificar o compilador de que certos métodos e funções estão disponíveis. No entanto, se você permitir que o compilador de F# deduza seus tipos de parâmetros genéricos, ele determinará as restrições apropriadas a você. Para saber mais, veja [Restrições](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Parâmetros de tipo resolvidos estaticamente

Há dois tipos de parâmetros de tipo que podem ser usados em programas em F#. O primeiro são os parâmetros de tipo genérico do tipo descrito nas seções anteriores. Esse primeiro tipo de parâmetro de tipo é equivalente a parâmetros de tipo genérico usados em linguagens como Visual Basic e C#. Outro tipo de parâmetro de tipo é específico do F# e é conhecido como um *parâmetro de tipo resolvido estaticamente*. Para saber mais sobre essas construções, veja [Parâmetros de tipo resolvidos estaticamente](statically-resolved-type-parameters.md).

## <a name="examples"></a>Exemplos

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Consulte também

- [Referência de Linguagem](../index.md)
- [Tipos](../fsharp-types.md)
- [Parâmetros de tipo resolvidos estaticamente](statically-resolved-type-parameters.md)
- [Genéricos no .NET Framework](~/docs/standard/generics/index.md)
- [Generalização Automática](automatic-generalization.md)
- [Restrições](constraints.md)
