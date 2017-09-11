---
title: "Genéricos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
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
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="6187f-102">Genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6187f-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="6187f-103">Genéricos foram adicionados à versão 2.0 da linguagem C# e o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6187f-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="6187f-104">Genéricos apresentam ao .NET Framework o conceito de parâmetros de tipo, que possibilitam a criação de classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou método seja declarado e instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="6187f-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="6187f-105">Por exemplo, ao usar um parâmetro de tipo genérico T, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer o custo ou corre o risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="6187f-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 <span data-ttu-id="6187f-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6187f-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="generics-overview"></a><span data-ttu-id="6187f-107">Visão geral de genéricos</span><span class="sxs-lookup"><span data-stu-id="6187f-107">Generics Overview</span></span>  
  
-   <span data-ttu-id="6187f-108">Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="6187f-108">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="6187f-109">O uso mais comum de genéricos é para criar classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="6187f-109">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="6187f-110">A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="6187f-110">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="6187f-111">Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="6187f-111">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="6187f-112">Você pode criar suas próprias interfaces genéricas, classes, métodos, eventos e delegados.</span><span class="sxs-lookup"><span data-stu-id="6187f-112">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="6187f-113">Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.</span><span class="sxs-lookup"><span data-stu-id="6187f-113">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="6187f-114">Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="6187f-114">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6187f-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6187f-115">Related Sections</span></span>  
 <span data-ttu-id="6187f-116">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="6187f-116">For more information:</span></span>  
  
-   [<span data-ttu-id="6187f-117">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="6187f-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="6187f-118">Benefícios dos genéricos</span><span class="sxs-lookup"><span data-stu-id="6187f-118">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="6187f-119">Parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="6187f-119">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="6187f-120">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="6187f-120">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="6187f-121">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="6187f-121">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="6187f-122">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="6187f-122">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="6187f-123">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="6187f-123">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="6187f-124">Delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="6187f-124">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="6187f-125">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="6187f-125">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="6187f-126">Genéricos e reflexão</span><span class="sxs-lookup"><span data-stu-id="6187f-126">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="6187f-127">Genéricos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6187f-127">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="6187f-128">Genéricos na biblioteca de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6187f-128">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6187f-129">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6187f-129">C# Language Specification</span></span>  
 <span data-ttu-id="6187f-130">Para obter mais informações, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6187f-130">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6187f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6187f-131">See Also</span></span>  
 <span data-ttu-id="6187f-132"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="6187f-132"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="6187f-133">[Guia de programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6187f-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6187f-134">[Tipos](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="6187f-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="6187f-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span><span class="sxs-lookup"><span data-stu-id="6187f-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span></span>  
 [<span data-ttu-id="6187f-136">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="6187f-136">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

