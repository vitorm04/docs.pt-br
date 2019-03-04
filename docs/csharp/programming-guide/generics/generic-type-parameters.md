---
title: Parâmetros de tipo genérico – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: f6acbfee5c6b5ec426076d7bf766a3c6894b736f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972177"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="2d223-102">Parâmetros de tipo genérico (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2d223-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="2d223-103">Na definição de um tipo genérico ou método, parâmetros de tipo são um espaço reservado para um tipo específico que o um cliente especifica ao instanciar uma variável do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="2d223-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="2d223-104">Uma classe genérica, como `GenericList<T>`, listada em [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md), não pode ser usada no estado em que se encontra porque não é realmente um tipo, mas um plano gráfico de um tipo.</span><span class="sxs-lookup"><span data-stu-id="2d223-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="2d223-105">Para usar `GenericList<T>`, o código cliente deve declarar e instanciar um tipo construído, especificando um argumento de tipo entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="2d223-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="2d223-106">O argumento de tipo para essa classe específica pode ser qualquer tipo reconhecido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="2d223-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="2d223-107">É possível criar qualquer quantidade de instâncias do tipo construído, cada uma usando um argumento de tipo diferente, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2d223-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
 <span data-ttu-id="2d223-108">Em cada uma dessas instâncias de `GenericList<T>`, todas as ocorrências de `T` na classe serão substituídas em tempo de execução com o argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="2d223-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="2d223-109">Por meio dessa substituição, cria-se três objetos separados eficientes e fortemente tipados usando uma única definição de classe.</span><span class="sxs-lookup"><span data-stu-id="2d223-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="2d223-110">Para obter mais informações sobre como essa substituição é executada pelo CLR, consulte [Genéricos em Tempo de Execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="2d223-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="2d223-111">Diretrizes para a Nomenclatura de Parâmetros de Tipo</span><span class="sxs-lookup"><span data-stu-id="2d223-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="2d223-112">**Nomeie** parâmetros de tipo genérico com nomes descritivos, a menos que um nome com uma única letra seja autoexplicativo e um nome descritivo não agregue valor.</span><span class="sxs-lookup"><span data-stu-id="2d223-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
-   <span data-ttu-id="2d223-113">**Considere** usar T como o nome do parâmetro de tipo em tipos com parâmetro de tipo de uma letra.</span><span class="sxs-lookup"><span data-stu-id="2d223-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
-   <span data-ttu-id="2d223-114">**Insira** o prefixo “T” em nomes descritivos de parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="2d223-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
-   <span data-ttu-id="2d223-115">**Considere** indicar as restrições colocadas em um parâmetro de tipo no nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2d223-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="2d223-116">Por exemplo, um parâmetro restrito a `ISession` pode ser chamado `TSession`.</span><span class="sxs-lookup"><span data-stu-id="2d223-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d223-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d223-117">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="2d223-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2d223-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2d223-119">Genéricos</span><span class="sxs-lookup"><span data-stu-id="2d223-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="2d223-120">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="2d223-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
