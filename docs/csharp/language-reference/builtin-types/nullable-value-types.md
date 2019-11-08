---
title: Tipos de valor Anulável C# -referência
description: Saiba mais C# sobre os tipos de valor anulável e como usá-los
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: b9400cd76eb0430dbe9c278e835a3cec7f9f131e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741161"
---
# <a name="nullable-value-types-c-reference"></a>Tipos de valores anuláveis (C# referência)

Um tipo de valor anulável `T?` representa todos os valores de seu [tipo de valor](../keywords/value-types.md) subjacente `T` e um valor [nulo](../keywords/null.md) adicional. Por exemplo, você pode atribuir qualquer um dos três valores a seguir a uma `bool?` variável: `true`, `false`ou `null`. Um tipo de valor subjacente `T` não pode ser um tipo de valor anulável em si.

> [!NOTE]
> C#8,0 apresenta o recurso de tipos de referência anulável. Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md). Os tipos de valor anulável estão disponíveis a C# partir de 2.

Qualquer tipo de valor anulável é uma instância da estrutura de <xref:System.Nullable%601?displayProperty=nameWithType> genérica. Você pode se referir a um tipo de valor anulável com um tipo subjacente `T` em qualquer um dos seguintes formulários intercambiáveis: `Nullable<T>` ou `T?`.

Normalmente, você usa um tipo de valor anulável quando precisa representar o valor indefinido de um tipo de valor subjacente. Por exemplo, um booliano ou `bool`variável só pode ser `true` ou `false`. No entanto, em alguns aplicativos, um valor de variável pode ser indefinido ou estar ausente. Por exemplo, um campo de banco de dados pode conter `true` ou `false`ou não pode conter nenhum valor, ou seja, `NULL`. Você pode usar o tipo de `bool?` nesse cenário.

## <a name="declaration-and-assignment"></a>Declaração e atribuição

Como um tipo de valor é implicitamente conversível para o tipo de valor anulável correspondente, você pode atribuir um valor a uma variável de um tipo de valor anulável, como faria com o tipo de valor subjacente. Você também pode atribuir o valor `null`. Por exemplo:

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

O valor padrão de um tipo de valor anulável representa `null`, ou seja, é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> retorna `false`.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Exame de uma instância de um tipo de valor anulável

A partir C# do 7,0, você pode usar o [operador de`is` com um padrão de tipo](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) para examinar uma instância de um tipo de valor anulável para `null` e recuperar um valor de um tipo subjacente:

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

Você sempre pode usar as seguintes propriedades somente leitura para examinar e obter um valor de uma variável de tipo de valor anulável:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indica se uma instância de um tipo de valor anulável tem um valor de seu tipo subjacente.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`. Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.

O exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-la:

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

Você também pode comparar uma variável de um tipo de valor anulável com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversão de um tipo de valor anulável para um tipo subjacente

Se você quiser atribuir um valor de tipo de valor anulável a uma variável de tipo de valor não anulável, talvez seja necessário especificar o valor a ser atribuído no lugar de `null`. Use o [operador de União nulo `??`](../operators/null-coalescing-operator.md) para fazer isso (você também pode usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para a mesma finalidade):

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

Se você quiser usar o valor [padrão](../keywords/default-values-table.md) do tipo de valor subjacente no lugar de `null`, use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.

Você também pode converter explicitamente um tipo de valor anulável para um tipo não anulável, como mostra o exemplo a seguir:

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

Em tempo de execução, se o valor de um tipo de valor anulável for `null`, a conversão explícita lançará um <xref:System.InvalidOperationException>.

Um tipo de valor não anulável `T` é implicitamente conversível para o tipo de valor anulável correspondente `T?`.

## <a name="lifted-operators"></a>Operadores levantados

Os operadores unários e binários predefinidos ou quaisquer operadores sobrecarregados com suporte de um tipo de valor `T` também são suportados pelo tipo de valor anulável correspondente `T?`. Esses operadores, também conhecidos como *operadores levantados*, produzem `null` se um ou ambos os operandos forem `null`; caso contrário, o operador usa os valores contidos de seus operandos para calcular o resultado. Por exemplo:

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Para o tipo de `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nesta seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo que um dos operandos seja `null`. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).

Para os [operadores de comparação](../operators/comparison-operators.md) `<`, `>`, `<=`e `>=`, se um ou ambos os operandos forem `null`, o resultado será `false`; caso contrário, os valores contidos dos operandos serão comparados. Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`. O exemplo a seguir mostra que 10

- Nem maior ou igual a `null`
- Nem menor que `null`

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

O exemplo anterior também mostra que uma comparação de igualdade de duas instâncias de tipo de valor anulável que são `null` são avaliadas como `true`.

Se existir uma [conversão definida pelo usuário](../operators/user-defined-conversion-operators.md) entre dois tipos de valor, a mesma conversão também poderá ser usada entre os tipos de valores anuláveis correspondentes.

## <a name="boxing-and-unboxing"></a>Conversões boxing e unboxing

Uma instância de um tipo de valor anulável `T?` é [a](../../programming-guide/types/boxing-and-unboxing.md) seguinte:

- Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.
- Se <xref:System.Nullable%601.HasValue%2A> retornar `true`, o valor correspondente do tipo de valor subjacente `T` será in a box, não a instância de <xref:System.Nullable%601>.

Você pode unbox um valor em caixa de um tipo de valor `T` para o tipo de valor anulável correspondente `T?`, como mostra o exemplo a seguir:

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Como identificar um tipo de valor anulável

O exemplo a seguir mostra como determinar se uma instância de <xref:System.Type?displayProperty=nameWithType> representa um tipo de valor anulável construído, ou seja, o tipo de <xref:System.Nullable%601?displayProperty=nameWithType> com um parâmetro de tipo especificado `T`:

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

Como mostra o exemplo, você usa o operador [typeof](../operators/type-testing-and-cast.md#typeof-operator) para criar uma instância de <xref:System.Type?displayProperty=nameWithType>.

Se você quiser determinar se uma instância é de um tipo de valor anulável, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância de <xref:System.Type> a ser testada com o código anterior. Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo de valor anulável, a instância é [encaixada](#boxing-and-unboxing) para <xref:System.Object>. Como Boxing de uma instância não nula de um tipo de valor anulável é equivalente à Boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna uma instância de <xref:System.Type> que representa o tipo subjacente de um tipo de valor anulável:

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

Além disso, não use o operador [is](../operators/type-testing-and-cast.md#is-operator) para determinar se uma instância é de um tipo de valor anulável. Como mostra o exemplo a seguir, você não pode distinguir tipos de uma instância de tipo de valor anulável e sua instância de tipo subjacente com o operador de `is`:

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulável:

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Os métodos descritos nesta seção não são aplicáveis no caso de tipos de [referência anuláveis](../../nullable-references.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos que permitem valor nulo](~/_csharplang/spec/types.md#nullable-types)
- [Operadores levantados](~/_csharplang/spec/expressions.md#lifted-operators)
- [Conversões anuláveis implícitas](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Conversões anuláveis explícitas](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Operadores de conversão levantados](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [O que exatamente "levantado" significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Tipos de referência nula](../../nullable-references.md)
