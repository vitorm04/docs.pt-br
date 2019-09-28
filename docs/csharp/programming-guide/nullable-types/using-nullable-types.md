---
title: Usando tipos de valor Anulável C# -guia de programação
ms.custom: seodec18
description: Saiba como trabalhar com tipos C# de valor anulável
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396169"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>Usando tipos de valor AnulávelC# (guia de programação)

Tipos de valor anulável são tipos que representam todos os valores de um tipo de valor subjacente `T` e um valor [nulo](../../language-reference/keywords/null.md) adicional. Para obter mais informações, consulte o tópico [tipos de valor anulável](index.md) .

> [!NOTE]
> C#8,0 apresenta o recurso de tipos de referência anulável. Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md). Os tipos de valor anulável estão disponíveis a C# partir de 2.

Você pode se referir a um tipo de valor anulável em qualquer um dos seguintes formulários intercambiáveis: `Nullable<T>` ou `T?`. `T` deve ser um tipo de valor.

## <a name="declaration-and-assignment"></a>Declaração e atribuição

Como um tipo de valor pode ser convertido implicitamente no tipo de valor anulável correspondente, você atribui um valor a um tipo anulável como você faria para o tipo de valor subjacente. Você também pode atribuir o valor `null`. Por exemplo:

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Exame de um valor de tipo que permite valor nulo

Use as seguintes propriedades ReadOnly para examinar uma instância de um tipo de valor anulável para NULL e recuperar um valor de um tipo subjacente:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Indica se uma instância de um tipo que permite valor nulo tem um valor de seu tipo subjacente.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`. Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.

O código no exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

Você também pode comparar uma variável de um tipo de valor anulável com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

A partir C# do 7,0, você pode usar a [correspondência de padrões](../../pattern-matching.md) para examinar e obter um valor de um tipo de valor anulável:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversão de um tipo de valor anulável para um tipo subjacente

Se você precisar atribuir um valor de um tipo de valor anulável a um tipo não anulável, use o [operador de União nula `??`](../../language-reference/operators/null-coalescing-operator.md) para especificar o valor a ser atribuído se um valor de um tipo de valor anulável for nulo (você também poderá usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para fazer isso) :

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de um tipo de valor anulável for `null` deve ser o valor padrão do tipo de valor subjacente.

Você pode converter explicitamente um tipo de valor anulável em um tipo não anulável. Por exemplo:

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

Em tempo de execução, se o valor de um tipo de valor anulável for `null`, a conversão explícita lançará um <xref:System.InvalidOperationException>.

Um tipo de valor que não permite valor nulo é convertido implicitamente no tipo que permite valor nulo correspondente.

## <a name="operators"></a>Operadores

Os operadores unários e binários predefinidos e quaisquer operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos anuláveis correspondentes. Esses operadores produzem `null` se um ou ambos os operandos forem `null`; caso contrário, o operador usará os valores contidos para calcular o resultado. Por exemplo:

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Para o tipo `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nesta seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo que um dos operandos seja `null`. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../../language-reference/operators/boolean-logical-operators.md).
  
Para os operadores relacionais (`<`, `>`, `<=`, `>=`), se um ou ambos os operandos forem `null`, o resultado será `false`. Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`. O exemplo a seguir mostra que 10

- Nem maior ou igual a `null`,
- Nem menor que `null`.

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

O exemplo acima também mostra que uma comparação de igualdade de dois tipos de valores anuláveis nulos é avaliada como `true`.

Para obter mais informações, confira a seção [Operadores suspensos](~/_csharplang/spec/expressions.md#lifted-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Conversões boxing e unboxing

Um tipo de valor que permite valor nulo passa pela [conversão boxing](../types/boxing-and-unboxing.md) por meio das seguintes regras:

- Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.
- Se <xref:System.Nullable%601.HasValue%2A> retorna `true`, um valor do tipo de valor subjacente `T` passa pela conversão boxing, não a instância de <xref:System.Nullable%601>.

Você pode aplicar a conversão unboxing no tipo de valor que passou pela conversão boxing convertendo-a no tipo que permite valor nulo correspondente, como mostra o exemplo a seguir:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Consulte também

- [Tipos de valor anuláveis](index.md)
- [O que exatamente "levantado" significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
