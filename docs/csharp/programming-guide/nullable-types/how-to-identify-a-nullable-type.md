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
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="5fcd4-103">Como identificar um tipo de valor anulável (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="5fcd4-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="5fcd4-104">O exemplo a seguir mostra como determinar se uma instância <xref:System.Type?displayProperty=nameWithType> representa um tipo de valor anulável genérico fechado, ou seja, o tipo de <xref:System.Nullable%601?displayProperty=nameWithType> com um parâmetro de tipo especificado `T`:</span><span class="sxs-lookup"><span data-stu-id="5fcd4-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="5fcd4-105">Como mostra o exemplo, o operador [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) é usado para criar um objeto <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fcd4-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="5fcd4-106">Se você quiser determinar se uma instância é de um tipo de valor anulável, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância <xref:System.Type> a ser testada com o código anterior.</span><span class="sxs-lookup"><span data-stu-id="5fcd4-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="5fcd4-107">Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo de valor anulável, a instância é [encaixada](using-nullable-types.md#boxing-and-unboxing) em <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5fcd4-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="5fcd4-108">Como a Boxing de uma instância não nula de um tipo de valor anulável é equivalente à Boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna um objeto <xref:System.Type> que representa o tipo subjacente de um tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="5fcd4-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="5fcd4-109">Não use o operador [is](../../language-reference/keywords/is.md) para determinar se uma instância é de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="5fcd4-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="5fcd4-110">Como mostra o exemplo a seguir, não é possível distinguir tipos de instâncias de um tipo de valor anulável e seu tipo subjacente com o uso do operador `is`:</span><span class="sxs-lookup"><span data-stu-id="5fcd4-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="5fcd4-111">Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="5fcd4-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="5fcd4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fcd4-112">See also</span></span>

- [<span data-ttu-id="5fcd4-113">Tipos de valor anuláveis</span><span class="sxs-lookup"><span data-stu-id="5fcd4-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="5fcd4-114">Usando tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="5fcd4-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
