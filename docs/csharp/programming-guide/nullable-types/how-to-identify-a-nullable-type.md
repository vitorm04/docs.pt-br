---
title: Como identificar um tipo de valor anulável – guia C# de programação
ms.custom: seodec18
description: Saiba como determinar se um tipo é um tipo de valor anulável ou uma instância é de um tipo de valor anulável
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392612"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>Como identificar um tipo de valor anulável (C# guia de programação)

O exemplo a seguir mostra como determinar se uma instância <xref:System.Type?displayProperty=nameWithType> representa um tipo de valor anulável genérico fechado, ou seja, o tipo de <xref:System.Nullable%601?displayProperty=nameWithType> com um parâmetro de tipo especificado `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Como mostra o exemplo, o operador [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) é usado para criar um objeto <xref:System.Type?displayProperty=nameWithType>.

Se você quiser determinar se uma instância é de um tipo de valor anulável, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância <xref:System.Type> a ser testada com o código anterior. Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo de valor anulável, a instância é [encaixada](using-nullable-types.md#boxing-and-unboxing) em <xref:System.Object>. Como a Boxing de uma instância não nula de um tipo de valor anulável é equivalente à Boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna um objeto <xref:System.Type> que representa o tipo subjacente de um tipo de valor anulável:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Não use o operador [is](../../language-reference/keywords/is.md) para determinar se uma instância é de um tipo de valor anulável. Como mostra o exemplo a seguir, não é possível distinguir tipos de instâncias de um tipo de valor anulável e seu tipo subjacente com o uso do operador `is`:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulável:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>Consulte também

- [Tipos de valor anuláveis](index.md)
- [Usando tipos de valor anulável](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
