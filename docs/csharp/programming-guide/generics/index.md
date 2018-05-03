---
title: Genéricos (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 026b8350a75794cf1101bef69d1bf15f474f103d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="c66cb-102">Genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c66cb-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="c66cb-103">Genéricos foram adicionados à versão 2.0 da linguagem C# e o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c66cb-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="c66cb-104">Genéricos apresentam ao .NET Framework o conceito de parâmetros de tipo, que possibilitam a criação de classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou método seja declarado e instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="c66cb-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="c66cb-105">Por exemplo, ao usar um parâmetro de tipo genérico T, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer o custo ou corre o risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="c66cb-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="c66cb-106">Visão geral de genéricos</span><span class="sxs-lookup"><span data-stu-id="c66cb-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="c66cb-107">Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="c66cb-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="c66cb-108">O uso mais comum de genéricos é para criar classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="c66cb-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="c66cb-109">A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="c66cb-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="c66cb-110">Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="c66cb-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="c66cb-111">Você pode criar suas próprias interfaces genéricas, classes, métodos, eventos e delegados.</span><span class="sxs-lookup"><span data-stu-id="c66cb-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="c66cb-112">Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.</span><span class="sxs-lookup"><span data-stu-id="c66cb-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="c66cb-113">Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="c66cb-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c66cb-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c66cb-114">Related Sections</span></span>  
 <span data-ttu-id="c66cb-115">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="c66cb-115">For more information:</span></span>  
  
-   [<span data-ttu-id="c66cb-116">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="c66cb-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="c66cb-117">Benefícios dos genéricos</span><span class="sxs-lookup"><span data-stu-id="c66cb-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="c66cb-118">Parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="c66cb-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="c66cb-119">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="c66cb-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="c66cb-120">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="c66cb-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="c66cb-121">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="c66cb-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="c66cb-122">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="c66cb-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="c66cb-123">Delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="c66cb-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="c66cb-124">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="c66cb-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="c66cb-125">Genéricos e reflexão</span><span class="sxs-lookup"><span data-stu-id="c66cb-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="c66cb-126">Genéricos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c66cb-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c66cb-127">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c66cb-127">C# Language Specification</span></span>  
 <span data-ttu-id="c66cb-128">Para obter mais informações, consulte a [Especificação da linguagem C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c66cb-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66cb-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c66cb-129">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="c66cb-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c66cb-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c66cb-131">Tipos</span><span class="sxs-lookup"><span data-stu-id="c66cb-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="c66cb-132">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="c66cb-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="c66cb-133">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="c66cb-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [<span data-ttu-id="c66cb-134">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="c66cb-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  