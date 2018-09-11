---
title: Como identificar um tipo que permite valor nulo (Guia de programação em C#)
description: Saiba como determinar se um tipo ou uma instância é de um tipo que permite valor nulo
ms.date: 08/06/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: c65f80974154d81b5ddf239b617eeeda68434e09
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178231"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Como identificar um tipo que permite valor nulo (Guia de programação em C#)

O exemplo a seguir mostra como determinar se uma instância de <xref:System.Type?displayProperty=nameWithType> representa um tipo que permite valor nulo:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Como mostra o exemplo, o operador [typeof](../../language-reference/keywords/typeof.md) é usado para criar um objeto <xref:System.Type?displayProperty=nameWithType>.  
  
Se você quiser determinar se uma instância é de um tipo que permite valor nulo, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância <xref:System.Type> a ser testada com o código anterior. Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo que permite valor nulo, a instância passa pela [conversão boxing](using-nullable-types.md#boxing-and-unboxing) em <xref:System.Object>. Como a conversão boxing de uma instância não nula de um tipo que permite valor nulo é equivalente à conversão boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna um objeto <xref:System.Type> que representa o tipo subjacente de um tipo que permite valor nulo:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Não use o operador [is](../../language-reference/keywords/is.md) para determinar se uma instância é de um tipo que permite valor nulo. Como mostra o exemplo a seguir, não é possível distinguir os tipos de instâncias de um tipo que permite valor nulo e seu tipo subjacente usando o operador `is`:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo que permite valor nulo:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Consulte também

- [Tipos que permitem valor nulo](index.md)  
- [Usando tipos que permitem valor nulo](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
