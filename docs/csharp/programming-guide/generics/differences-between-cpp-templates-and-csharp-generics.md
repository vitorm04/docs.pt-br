---
title: "Diferenças entre modelos C++ e genéricos C# (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 483d33531141127e083c5b75789f405427e46890
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="97f0b-102">Diferenças entre modelos C++ e genéricos C# (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="97f0b-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="97f0b-103">Os modelos C++ e genéricos C# são recursos de linguagem que fornecem o suporte aos tipos parametrizados.</span><span class="sxs-lookup"><span data-stu-id="97f0b-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="97f0b-104">No entanto, há várias diferenças entre os dois.</span><span class="sxs-lookup"><span data-stu-id="97f0b-104">However, there are many differences between the two.</span></span> <span data-ttu-id="97f0b-105">No nível de sintaxe, os genéricos C# são uma abordagem mais simples para os tipos parametrizados sem a complexidade de modelos C++.</span><span class="sxs-lookup"><span data-stu-id="97f0b-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="97f0b-106">Além disso, o C# não tenta fornecer toda a funcionalidade que os modelos C++ fornecem.</span><span class="sxs-lookup"><span data-stu-id="97f0b-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="97f0b-107">No nível da implementação, a principal diferença é que as substituições do tipo genérico do C# são realizadas em tempo de execução e as informações do tipo genérico são preservadas para objetos instanciados.</span><span class="sxs-lookup"><span data-stu-id="97f0b-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="97f0b-108">Para obter mais informações, consulte [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="97f0b-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="97f0b-109">A seguir estão as principais diferenças entre modelos C++ e genéricos C#:</span><span class="sxs-lookup"><span data-stu-id="97f0b-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="97f0b-110">Os genéricos C# não oferecem a mesma flexibilidade que os modelos C++.</span><span class="sxs-lookup"><span data-stu-id="97f0b-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="97f0b-111">Por exemplo, não é possível chamar os operadores aritméticos em uma classe genérica C#, embora seja possível chamar operadores definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="97f0b-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="97f0b-112">O C# não permite parâmetros de modelo sem tipo, como `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="97f0b-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="97f0b-113">O C# não dá suporte à especialização explícita ou seja, uma implementação personalizada de um modelo para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="97f0b-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="97f0b-114">O C# não dá suporte à especialização parcial: uma implementação personalizada para um subconjunto dos argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="97f0b-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="97f0b-115">O C# não permite que o parâmetro de tipo a ser usado como a classe base para o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="97f0b-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="97f0b-116">O C# não permite que os parâmetros de tipo tenham tipos padrão.</span><span class="sxs-lookup"><span data-stu-id="97f0b-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="97f0b-117">No C#, um parâmetro de tipo genérico não pode ser genérico, embora os tipos construídos possam ser usados como genéricos.</span><span class="sxs-lookup"><span data-stu-id="97f0b-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="97f0b-118">O C++ permite parâmetros de modelo.</span><span class="sxs-lookup"><span data-stu-id="97f0b-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="97f0b-119">O C++ permite o código que pode não ser válido para todos os parâmetros de tipo no modelo, que é então verificado para o tipo específico usado como o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="97f0b-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="97f0b-120">O C# requer código em uma classe a ser gravada de forma que ele funcionará com qualquer tipo que satisfaça as restrições.</span><span class="sxs-lookup"><span data-stu-id="97f0b-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="97f0b-121">Por exemplo, em C++ é possível escrever uma função que usa os operadores aritméticos `+` e `-` em objetos do parâmetro de tipo, que produzirá um erro no momento da instanciação do modelo com um tipo que não dá suporte a esses operadores.</span><span class="sxs-lookup"><span data-stu-id="97f0b-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="97f0b-122">O C# não permite isso. Os únicos constructos da linguagem permitidos são os que podem ser deduzidos das restrições.</span><span class="sxs-lookup"><span data-stu-id="97f0b-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f0b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97f0b-123">See Also</span></span>  
 <span data-ttu-id="97f0b-124">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="97f0b-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="97f0b-125">[Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="97f0b-125">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 [<span data-ttu-id="97f0b-126">Modelos</span><span class="sxs-lookup"><span data-stu-id="97f0b-126">Templates</span></span>](/cpp/cpp/templates-cpp)

