---
title: "Genéricos e atributos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e6fdd32fb41c3bda83e848952f70cbd736a0fc60
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="97189-102">Genéricos e atributos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="97189-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="97189-103">Atributos podem ser aplicados a tipos genéricos da mesma forma que a tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="97189-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="97189-104">Para obter mais informações sobre a aplicação de atributos, consulte [Atributos](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="97189-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="97189-105">Atributos personalizados são permitidos somente para referenciar tipos genéricos abertos, que são tipos genéricos para os quais nenhum argumento de tipo é fornecido e tipos genéricos construídos fechados, que fornecem argumentos para todos os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="97189-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="97189-106">Os exemplos a seguir usam esse atributo personalizado:</span><span class="sxs-lookup"><span data-stu-id="97189-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="97189-107">Um atributo pode referenciar um tipo genérico aberto:</span><span class="sxs-lookup"><span data-stu-id="97189-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="97189-108">Especifica vários parâmetros de tipo usando a quantidade apropriada de vírgulas.</span><span class="sxs-lookup"><span data-stu-id="97189-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="97189-109">Neste exemplo, `GenericClass2` tem dois parâmetros de tipo:</span><span class="sxs-lookup"><span data-stu-id="97189-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="97189-110">Um atributo pode referenciar um tipo genérico construído fechado:</span><span class="sxs-lookup"><span data-stu-id="97189-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="97189-111">Um atributo que referencia um parâmetro de tipo genérico causará um erro em tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="97189-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="97189-112">Um tipo genérico não pode herdar de <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="97189-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="97189-113">Para obter informações sobre um tipo genérico ou um parâmetro de tipo em tempo de execução, é possível usar os métodos do <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="97189-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="97189-114">Para obter mais informações, consulte [Genéricos e Reflexão](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="97189-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97189-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97189-115">See Also</span></span>  
 [<span data-ttu-id="97189-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="97189-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="97189-117">Genéricos</span><span class="sxs-lookup"><span data-stu-id="97189-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="97189-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="97189-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
