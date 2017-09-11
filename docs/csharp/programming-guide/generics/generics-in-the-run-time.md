---
title: "Genéricos em tempo de execução (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
caps.latest.revision: 18
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
ms.openlocfilehash: 661dff2d8ec2e12ab6a459660a5378f74e93b9c5
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="generics-in-the-run-time-c-programming-guide"></a><span data-ttu-id="f6dc7-102">Genéricos em tempo de execução (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f6dc7-102">Generics in the Run Time (C# Programming Guide)</span></span>
<span data-ttu-id="f6dc7-103">Um tipo genérico ou método compilado em Microsoft Intermediate Language (MSIL) conterá metadados que o identificarão como possuidor de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-103">When a generic type or method is compiled into Microsoft intermediate language (MSIL), it contains metadata that identifies it as having type parameters.</span></span> <span data-ttu-id="f6dc7-104">O uso de MSIL em um tipo genérico será diferente de acordo com o parâmetro de tipo fornecido, ou seja, se ele é um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-104">How the MSIL for a generic type is used differs based on whether the supplied type parameter is a value type or reference type.</span></span>  
  
 <span data-ttu-id="f6dc7-105">Quando um tipo genérico é construído pela primeira vez com um tipo de valor como parâmetro, o tempo de execução cria um tipo genérico especializado com o(s) parâmetro(s) fornecido(s) substituído(s) nos locais apropriados do MSIL.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-105">When a generic type is first constructed with a value type as a parameter, the runtime creates a specialized generic type with the supplied parameter or parameters substituted in the appropriate locations in the MSIL.</span></span> <span data-ttu-id="f6dc7-106">Os tipos genéricos especializados são criados uma vez para cada tipo de valor único usado como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-106">Specialized generic types are created one time for each unique value type that is used as a parameter.</span></span>  
  
 <span data-ttu-id="f6dc7-107">Por exemplo, caso o código do programa declarar uma pilha construída de inteiros:</span><span class="sxs-lookup"><span data-stu-id="f6dc7-107">For example, suppose your program code declared a stack that is constructed of integers:</span></span>  
  
 <span data-ttu-id="f6dc7-108">[!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-108">[!code-cs[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-109">Neste ponto, o tempo de execução gerará uma versão especializada da classe <xref:System.Collections.Generic.Stack%601> com o inteiro substituído corretamente, de acordo com seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-109">At this point, the runtime generates a specialized version of the <xref:System.Collections.Generic.Stack%601> class that has the integer substituted appropriately for its parameter.</span></span> <span data-ttu-id="f6dc7-110">Agora, sempre que o código do programa utilizar uma pilha de inteiros, o tempo de execução reutilizará a classe especializada <xref:System.Collections.Generic.Stack%601> gerada.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-110">Now, whenever your program code uses a stack of integers, the runtime reuses the generated specialized <xref:System.Collections.Generic.Stack%601> class.</span></span> <span data-ttu-id="f6dc7-111">No exemplo a seguir, são criadas duas instâncias de uma pilha de inteiros e eles compartilham uma única instância do código `Stack<int>`:</span><span class="sxs-lookup"><span data-stu-id="f6dc7-111">In the following example, two instances of a stack of integers are created, and they share a single instance of the `Stack<int>` code:</span></span>  
  
 <span data-ttu-id="f6dc7-112">[!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-112">[!code-cs[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-113">No entanto, suponha que outra classe <xref:System.Collections.Generic.Stack%601> com um tipo de valor diferente – como `long` ou uma estrutura definida pelo usuário como parâmetro – foi criada em outro ponto do código.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-113">However, suppose that another <xref:System.Collections.Generic.Stack%601> class with a different value type such as a `long` or a user-defined structure as its parameter is created at another point in your code.</span></span> <span data-ttu-id="f6dc7-114">Como resultado, o tempo de execução gerará outra versão do tipo genérico e substituirá um `long` nos locais apropriados no MSIL.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-114">As a result, the runtime generates another version of the generic type and substitutes a `long` in the appropriate locations in MSIL.</span></span> <span data-ttu-id="f6dc7-115">Conversões não são mais necessárias, pois cada classe genérica especializada contém o tipo de valor nativamente.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-115">Conversions are no longer necessary because each specialized generic class natively contains the value type.</span></span>  
  
 <span data-ttu-id="f6dc7-116">Os genéricos funcionam de outro modo nos tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-116">Generics work somewhat differently for reference types.</span></span> <span data-ttu-id="f6dc7-117">Na primeira vez em que um genérico é construído com qualquer tipo de referência, o tempo de execução cria um tipo genérico especializado com referências de objeto substituídas por parâmetros no MSIL.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-117">The first time a generic type is constructed with any reference type, the runtime creates a specialized generic type with object references substituted for the parameters in the MSIL.</span></span> <span data-ttu-id="f6dc7-118">Em seguida, sempre que um tipo construído for instanciado com um tipo de referência como parâmetro, independentemente do tipo, o tempo de execução reutilizará a versão especializada do tipo genérico criada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-118">Then, every time that a constructed type is instantiated with a reference type as its parameter, regardless of what type it is, the runtime reuses the previously created specialized version of the generic type.</span></span> <span data-ttu-id="f6dc7-119">Isso é possível porque todas as referências são do mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-119">This is possible because all references are the same size.</span></span>  
  
 <span data-ttu-id="f6dc7-120">Por exemplo, suponha que há dois tipos de referência, uma classe `Customer` e uma classe `Order` e que uma pilha de tipos `Customer` foi criada:</span><span class="sxs-lookup"><span data-stu-id="f6dc7-120">For example, suppose you had two reference types, a `Customer` class and an `Order` class, and also suppose that you created a stack of `Customer` types:</span></span>  
  
 <span data-ttu-id="f6dc7-121">[!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-121">[!code-cs[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-122">[!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-122">[!code-cs[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-123">Neste ponto, o tempo de execução gerará uma versão especializada da classe <xref:System.Collections.Generic.Stack%601> que armazenará referências de objeto que serão preenchidas posteriormente, em vez de armazenar dados.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-123">At this point, the runtime generates a specialized version of the <xref:System.Collections.Generic.Stack%601> class that stores object references that will be filled in later instead of storing data.</span></span> <span data-ttu-id="f6dc7-124">Suponha que a próxima linha de código crie uma pilha de outro tipo de referência, com o nome `Order`:</span><span class="sxs-lookup"><span data-stu-id="f6dc7-124">Suppose the next line of code creates a stack of another reference type, which is named `Order`:</span></span>  
  
 <span data-ttu-id="f6dc7-125">[!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-125">[!code-cs[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-126">Ao contrário dos tipos de valor, outra versão especializada da classe <xref:System.Collections.Generic.Stack%601> não será criada para o tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-126">Unlike with value types, another specialized version of the <xref:System.Collections.Generic.Stack%601> class is not created for the `Order` type.</span></span> <span data-ttu-id="f6dc7-127">Em vez disso, uma instância da versão especializada da classe <xref:System.Collections.Generic.Stack%601> será criada e a variável `orders` será definida para referenciá-la.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-127">Instead, an instance of the specialized version of the <xref:System.Collections.Generic.Stack%601> class is created and the `orders` variable is set to reference it.</span></span> <span data-ttu-id="f6dc7-128">Imagine que uma linha de código foi encontrada para criar uma pilha de um tipo `Customer`:</span><span class="sxs-lookup"><span data-stu-id="f6dc7-128">Suppose that you then encountered a line of code to create a stack of a `Customer` type:</span></span>  
  
 <span data-ttu-id="f6dc7-129">[!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6dc7-129">[!code-cs[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]</span></span>  
  
 <span data-ttu-id="f6dc7-130">Assim como acontece com o uso anterior da classe <xref:System.Collections.Generic.Stack%601> criada usando o tipo `Order`, outra instância da classe especializada <xref:System.Collections.Generic.Stack%601> é criada.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-130">As with the previous use of the <xref:System.Collections.Generic.Stack%601> class created by using the `Order` type, another instance of the specialized <xref:System.Collections.Generic.Stack%601> class is created.</span></span> <span data-ttu-id="f6dc7-131">Os ponteiros contidos nela são definidos para referenciar uma área de memória do tamanho de um tipo `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-131">The pointers that are contained therein are set to reference an area of memory the size of a `Customer` type.</span></span> <span data-ttu-id="f6dc7-132">Como a quantidade de tipos de referência pode variar muito entre os programas, a implementação de genéricos no C# reduz significativamente a quantidade de código ao diminuir para um o número de classes especializadas criadas pelo compilador para classes genéricas ou tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-132">Because the number of reference types can vary wildly from program to program, the C# implementation of generics greatly reduces the amount of code by reducing to one the number of specialized classes created by the compiler for generic classes of reference types.</span></span>  
  
 <span data-ttu-id="f6dc7-133">Além disso, quando uma classe genérica do C# for instanciada usando um tipo de valor ou parâmetro de tipo de referência, a reflexão pode consultá-la em tempo de execução e o seu tipo real e parâmetro de tipo podem ser determinados.</span><span class="sxs-lookup"><span data-stu-id="f6dc7-133">Moreover, when a generic C# class is instantiated by using a value type or reference type parameter, reflection can query it at runtime and both its actual type and its type parameter can be ascertained.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6dc7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6dc7-134">See Also</span></span>  
 <span data-ttu-id="f6dc7-135"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="f6dc7-135"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="f6dc7-136">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6dc7-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f6dc7-137">[Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="f6dc7-137">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 [<span data-ttu-id="f6dc7-138">Genéricos</span><span class="sxs-lookup"><span data-stu-id="f6dc7-138">Generics</span></span>](~/docs/standard/generics/index.md)

