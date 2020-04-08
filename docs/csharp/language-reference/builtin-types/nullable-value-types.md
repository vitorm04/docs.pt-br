---
title: Tipos de valor anulados - referência C#
description: Saiba mais sobre os tipos de valor nulo C# e como usá-los
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: c13ef6a091ec6aebd4608c5ed8d2c03b067c7312
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888066"
---
# <a name="nullable-value-types-c-reference"></a>Tipos de valor anulados (referência C#)

Um *tipo* `T?` de valor anulado representa todos os valores do seu [tipo](value-types.md) `T` de valor subjacente e um valor [nulo](../keywords/null.md) adicional. Por exemplo, você pode atribuir qualquer um `bool?` dos `true`três `false`valores a uma variável: , ou `null`. Um tipo `T` de valor subjacente não pode ser um tipo de valor anulado em si.

> [!NOTE]
> C# 8.0 introduz o recurso de tipos de referência anulados. Para obter mais informações, consulte [tipos de referência nulamente](nullable-reference-types.md). Os tipos de valor anulados estão disponíveis a partir de C# 2.

Qualquer tipo de valor anulado é <xref:System.Nullable%601?displayProperty=nameWithType> uma instância da estrutura genérica. Você pode consultar um tipo de valor `T` anulado com um tipo subjacente `Nullable<T>` `T?`em qualquer uma das seguintes formas intercambiáveis: ou .

Você normalmente usa um tipo de valor anulado quando precisa representar o valor indefinido de um tipo de valor subjacente. Por exemplo, uma variável `bool`booleana, `true` ou `false`, só pode ser ou . No entanto, em alguns aplicativos um valor variável pode ser indefinido ou ausente. Por exemplo, um campo `true` `false`de banco de dados pode conter ou `NULL`, ou pode conter nenhum valor, ou seja, . Você pode `bool?` usar o tipo nesse cenário.

## <a name="declaration-and-assignment"></a>Declaração e atribuição

Como um tipo de valor é implicitamente conversível para o tipo de valor nulo correspondente, você pode atribuir um valor a uma variável de um tipo de valor anulado como você faria para o seu tipo de valor subjacente. Você também pode atribuir o valor `null`. Por exemplo:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

O valor padrão de um tipo `null`de valor anulado representa, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> ou `false`seja, é uma instância cuja propriedade retorna.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Exame de uma instância de um tipo de valor anulado

Começando com C# 7.0, você pode usar o `null` [ `is` operador com um padrão de tipo](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) para examinar uma instância de um tipo de valor anulado e recuperar um valor de um tipo subjacente:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Você sempre pode usar as seguintes propriedades somente leitura para examinar e obter um valor de uma variável de tipo de valor anulado:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>indica se uma instância de um tipo de valor anulado tem um valor de seu tipo subjacente.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`. Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.

O exemplo a `HasValue` seguir usa a propriedade para testar se a variável contém um valor antes de exibi-la:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Você também pode comparar uma variável de `null` um tipo `HasValue` de valor anulado com em vez de usar a propriedade, como mostra o exemplo a seguir:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversão de um tipo de valor anulado para um tipo subjacente

Se você quiser atribuir um valor de um tipo de valor anulado a uma variável de tipo de valor `null`não anulado, talvez seja necessário especificar o valor a ser atribuído no lugar de . Use o [operador `??` de coalizão nula](../operators/null-coalescing-operator.md) para fazer isso <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (você também pode usar o método para o mesmo propósito):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Se você quiser usar o valor [padrão](default-values.md) do tipo `null`de <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> valor subjacente no lugar de , use o método.

Você também pode lançar explicitamente um tipo de valor anulado a um tipo não anulado, como mostra o exemplo a seguir:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

No tempo de execução, se o `null`valor de um <xref:System.InvalidOperationException>tipo de valor anulado for, o elenco explícito lança um .

Um tipo `T` de valor não anulado é implicitamente `T?`conversível para o tipo de valor nulo correspondente .

## <a name="lifted-operators"></a>Operadores suspensos

Os [operadores indefinidos](../operators/index.md) e binários predefinidos ou quaisquer operadores sobrecarregados que são suportados por um tipo de `T` valor também são suportados pelo tipo `T?`de valor nulo correspondente . Esses operadores, também conhecidos como `null` *operadores suspensos,* produzem `null`se um ou ambos os orperands são; caso contrário, o operador utiliza os valores contidos de seus operands para calcular o resultado. Por exemplo:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Para `bool?` o tipo, `&` os `|` operadores pré-definidos e os operadores não seguem as regras descritas nesta seção: o `null`resultado de uma avaliação do operador pode ser não nulo mesmo se um dos operands for . Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).

Para os [operadores](../operators/comparison-operators.md) `<` `<=`de `>=`comparação, `>`e, se um `null`ou ambos `false`os operands forem, o resultado é; caso contrário, os valores contidos de operands são comparados. Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`. O exemplo a seguir mostra que 10

- nem maior do que ou igual a`null`
- nem menos do que`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Para o [operador](../operators/equality-operators.md#equality-operator-) `==`da igualdade , se `null`ambos os `true`operands são , o `null`resultado é `false`, se apenas um dos operands é , o resultado é ; caso contrário, os valores contidos de operands são comparados.

Para o [operador](../operators/equality-operators.md#inequality-operator-) `!=`da desigualdade , se `null`ambos os `false`operands são , o `null`resultado é `true`, se apenas um dos operands é , o resultado é ; caso contrário, os valores contidos de operands são comparados.

Se existir uma [conversão definida pelo usuário](../operators/user-defined-conversion-operators.md) entre dois tipos de valor, a mesma conversão também pode ser usada entre os tipos de valor anulados correspondentes.

## <a name="boxing-and-unboxing"></a>Conversões boxing e unboxing

Uma instância de um `T?` tipo de valor anulado é [encaixotada](../../programming-guide/types/boxing-and-unboxing.md) da seguinte forma:

- Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.
- Se <xref:System.Nullable%601.HasValue%2A> `true`as devoluções, o valor `T` correspondente do tipo de <xref:System.Nullable%601>valor subjacente é encaixotado, não a instância de .

Você pode desembaficar um `T` valor em caixa de `T?`um tipo de valor para o tipo de valor anulado correspondente, como mostra o exemplo a seguir:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Como identificar um tipo de valor anulado

O exemplo a seguir mostra <xref:System.Type?displayProperty=nameWithType> como determinar se uma instância representa um <xref:System.Nullable%601?displayProperty=nameWithType> tipo de valor anulado `T`construído, ou seja, o tipo com um parâmetro de tipo especificado:

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Como o exemplo mostra, você usa o <xref:System.Type?displayProperty=nameWithType> [tipode](../operators/type-testing-and-cast.md#typeof-operator) operador para criar uma instância.

Se você quiser determinar se uma instância é de um tipo <xref:System.Object.GetType%2A?displayProperty=nameWithType> de valor <xref:System.Type> anulado, não use o método para obter uma instância a ser testada com o código anterior. Quando você <xref:System.Object.GetType%2A?displayProperty=nameWithType> chama o método em uma instância de um tipo <xref:System.Object>de valor anulado, a instância é [encaixotada](#boxing-and-unboxing) em . Como o boxe de uma instância não nula de um tipo de valor <xref:System.Object.GetType%2A> nulo <xref:System.Type> é equivalente ao boxe de um valor do tipo subjacente, retorna uma instância que representa o tipo subjacente de um tipo de valor nulo:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Além disso, não use o [operador do is](../operators/type-testing-and-cast.md#is-operator) para determinar se uma instância é de um tipo de valor anulado. Como o exemplo a seguir mostra, você não pode distinguir tipos de `is` uma instância de tipo de valor anulada e sua instância de tipo subjacente com o operador:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulado:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Os métodos descritos nesta seção não são aplicáveis no caso de tipos de [referência anulados](nullable-reference-types.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos anulados](~/_csharplang/spec/types.md#nullable-types)
- [Operadores suspensos](~/_csharplang/spec/expressions.md#lifted-operators)
- [Conversões anuladas implícitas](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Conversões anuladas explícitas](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Operadores de conversão levantados](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [O que exatamente "levantado" significa?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Tipos de referência anuláveis](nullable-reference-types.md)
