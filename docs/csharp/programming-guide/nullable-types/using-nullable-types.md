---
title: Uso de tipos que permitem valor nulo – Guia de programação em C#
ms.custom: seodec18
description: Saiba como trabalhar com tipos que permitem valor nulo do C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: ef7c9c18d303131b5a1c0156be820e1d475e7ec1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306645"
---
# <a name="using-nullable-types-c-programming-guide"></a>Usando tipos que permitem valor nulo (Guia de programação em C#)

Os tipos que permitem valor nulo representam todos os valores de um tipo de valor subjacente `T` e um valor [null](../../language-reference/keywords/null.md) adicional. Para obter mais informações, confira o tópico [Tipos que permitem valor nulo](index.md).

Você pode se referir a um tipo que permite valor nulo de uma destas formas: `Nullable<T>` ou `T?`. Essas duas formas são intercambiáveis.  
  
## <a name="declaration-and-assignment"></a>Declaração e atribuição

Como um tipo de valor pode ser convertido implicitamente no tipo que permite valor nulo correspondente, você pode atribuir um valor a um tipo que permite valor nulo como faria para seu tipo de valor subjacente. Você também pode atribuir o valor `null`.  Por exemplo:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Exame de um valor de tipo que permite valor nulo

Use as seguintes propriedades readonly para examinar se uma instância de um tipo que permite valor nulo é nula e recuperar um valor de um tipo subjacente:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Indica se uma instância de um tipo que permite valor nulo tem um valor de seu tipo subjacente.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`. Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.
  
O código no exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Você também pode comparar uma variável de tipo que permite valor nulo com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Começando no C# 7.0, você pode usar [correspondência de padrões](../../pattern-matching.md) tanto examinar e obter um valor de um tipo que permite valor nulo:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Conversão de um tipo que permite valor nulo em um tipo subjacente

Se você precisar atribuir um valor de tipo que permite valor nulo a um tipo que não permite valor nulo, use o [operador de união nula `??`](../../language-reference/operators/null-coalescing-operator.md) para especificar o valor a ser atribuído quando um valor de tipo que permite valor nulo for nulo (você também poderá usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para fazer isso):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo é nulo deve ser o valor padrão do tipo de valor subjacente.
  
Você pode converter explicitamente um tipo que permite valor nulo em um tipo que não permite valor nulo. Por exemplo:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

No tempo de execução, quando o valor de um tipo que permite valor nulo é nulo, a conversão explícita gera um <xref:System.InvalidOperationException>.

Um tipo de valor que não permite valor nulo é convertido implicitamente no tipo que permite valor nulo correspondente.
  
## <a name="operators"></a>Operadores

Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo. Esses operadores produzem um valor nulo quando um ou ambos os operandos são nulos. Caso contrário, o operador usa os valores contidos para calcular o resultado. Por exemplo:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Para o tipo `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nessa seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo quando um dos operandos é nulo. Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../../language-reference/operators/boolean-logical-operators.md).
  
Para os operadores relacionais (`<`, `>`, `<=` e `>=`), quando um ou ambos os operandos são nulos, o resultado é `false`. Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`. O exemplo a seguir mostra que 10

- não é maior nem igual a nulo,
- nem menor que nulo.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
O exemplo acima também mostra que uma comparação de igualdade de dois tipos que permitem valor nulo e são nulos é avaliada como `true`.

Para obter mais informações, confira a seção [Operadores suspensos](~/_csharplang/spec/expressions.md#lifted-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Conversões boxing e unboxing

Um tipo de valor que permite valor nulo passa pela [conversão boxing](../types/boxing-and-unboxing.md) por meio das seguintes regras:

- Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.  
- Se <xref:System.Nullable%601.HasValue%2A> retorna `true`, um valor do tipo de valor subjacente `T` passa pela conversão boxing, não a instância de <xref:System.Nullable%601>.

Você pode aplicar a conversão unboxing no tipo de valor que passou pela conversão boxing convertendo-a no tipo que permite valor nulo correspondente, como mostra o exemplo a seguir:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Consulte também

- [Tipos que permitem valor nulo](index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [O que exatamente "levantado" significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
