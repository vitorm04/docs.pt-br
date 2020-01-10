---
title: Genéricos e atributos – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703020"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="13759-102">Genéricos e atributos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="13759-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="13759-103">Atributos podem ser aplicados a tipos genéricos da mesma forma que a tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="13759-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="13759-104">Para obter mais informações sobre a aplicação de atributos, consulte [Atributos](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="13759-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="13759-105">Atributos personalizados são permitidos somente para referenciar tipos genéricos abertos, que são tipos genéricos para os quais nenhum argumento de tipo é fornecido e tipos genéricos construídos fechados, que fornecem argumentos para todos os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="13759-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="13759-106">Os exemplos a seguir usam esse atributo personalizado:</span><span class="sxs-lookup"><span data-stu-id="13759-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="13759-107">Um atributo pode referenciar um tipo genérico aberto:</span><span class="sxs-lookup"><span data-stu-id="13759-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="13759-108">Especifica vários parâmetros de tipo usando a quantidade apropriada de vírgulas.</span><span class="sxs-lookup"><span data-stu-id="13759-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="13759-109">Neste exemplo, `GenericClass2` tem dois parâmetros de tipo:</span><span class="sxs-lookup"><span data-stu-id="13759-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="13759-110">Um atributo pode referenciar um tipo genérico construído fechado:</span><span class="sxs-lookup"><span data-stu-id="13759-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="13759-111">Um atributo que referencia um parâmetro de tipo genérico causará um erro em tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="13759-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="13759-112">Um tipo genérico não pode herdar de <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="13759-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="13759-113">Para obter informações sobre um tipo genérico ou um parâmetro de tipo em tempo de execução, é possível usar os métodos do <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="13759-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="13759-114">Para obter mais informações, consulte [Genéricos e Reflexão](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="13759-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13759-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="13759-115">See also</span></span>

- [<span data-ttu-id="13759-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="13759-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13759-117">Genéricos</span><span class="sxs-lookup"><span data-stu-id="13759-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="13759-118">Atributos</span><span class="sxs-lookup"><span data-stu-id="13759-118">Attributes</span></span>](../../../standard/attributes/index.md)
