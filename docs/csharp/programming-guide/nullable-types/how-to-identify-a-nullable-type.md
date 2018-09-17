---
title: Como identificar um tipo que permite valor nulo (Guia de programação em C#)
description: Saiba como determinar se um tipo ou uma instância é de um tipo que permite valor nulo
ms.date: 08/06/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: c65f80974154d81b5ddf239b617eeeda68434e09
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45624938"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="9c5e3-103">Como identificar um tipo que permite valor nulo (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9c5e3-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="9c5e3-104">O exemplo a seguir mostra como determinar se uma instância de <xref:System.Type?displayProperty=nameWithType> representa um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="9c5e3-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a nullable type:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="9c5e3-105">Como mostra o exemplo, o operador [typeof](../../language-reference/keywords/typeof.md) é usado para criar um objeto <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9c5e3-105">As the example shows, you use the [typeof](../../language-reference/keywords/typeof.md) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="9c5e3-106">Se você quiser determinar se uma instância é de um tipo que permite valor nulo, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância <xref:System.Type> a ser testada com o código anterior.</span><span class="sxs-lookup"><span data-stu-id="9c5e3-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="9c5e3-107">Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo que permite valor nulo, a instância passa pela [conversão boxing](using-nullable-types.md#boxing-and-unboxing) em <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9c5e3-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="9c5e3-108">Como a conversão boxing de uma instância não nula de um tipo que permite valor nulo é equivalente à conversão boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna um objeto <xref:System.Type> que representa o tipo subjacente de um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="9c5e3-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="9c5e3-109">Não use o operador [is](../../language-reference/keywords/is.md) para determinar se uma instância é de um tipo que permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="9c5e3-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="9c5e3-110">Como mostra o exemplo a seguir, não é possível distinguir os tipos de instâncias de um tipo que permite valor nulo e seu tipo subjacente usando o operador `is`:</span><span class="sxs-lookup"><span data-stu-id="9c5e3-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="9c5e3-111">Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="9c5e3-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="9c5e3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c5e3-112">See Also</span></span>

- [<span data-ttu-id="9c5e3-113">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="9c5e3-113">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="9c5e3-114">Usando tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="9c5e3-114">Using nullable types</span></span>](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
