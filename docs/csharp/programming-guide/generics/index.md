---
title: Genéricos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589598"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="faba8-102">Genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="faba8-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="faba8-103">Genéricos foram adicionados à versão 2.0 da linguagem C# e o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="faba8-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="faba8-104">Genéricos apresentam ao .NET Framework o conceito de parâmetros de tipo, que possibilitam a criação de classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou método seja declarado e instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="faba8-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="faba8-105">Por exemplo, ao usar um parâmetro de tipo genérico T, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer o custo ou corre o risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="faba8-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="faba8-106">As classes e métodos genéricos combinam a capacidade de reutilização, a segurança de tipos e a eficiência de uma maneira que suas contrapartes não genéricas não conseguem.</span><span class="sxs-lookup"><span data-stu-id="faba8-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="faba8-107">Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas.</span><span class="sxs-lookup"><span data-stu-id="faba8-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="faba8-108">A versão 2.0 da biblioteca de classes do .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que contém várias classes de coleção novas com base em genéricos.</span><span class="sxs-lookup"><span data-stu-id="faba8-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="faba8-109">É recomendável que todos os aplicativos que se destinam ao .NET Framework 2.0 e posterior usem as novas classes de coleção genéricas em vez das homólogas não genéricas mais antigas, como a <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="faba8-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="faba8-110">Para saber mais, confira [Genéricos no .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="faba8-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="faba8-111">É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes.</span><span class="sxs-lookup"><span data-stu-id="faba8-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="faba8-112">O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="faba8-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="faba8-113">(Na maioria dos casos, você deve usar a classe <xref:System.Collections.Generic.List%601>, fornecida pela biblioteca de classes .NET Framework, em vez de criar a sua própria classe). O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista.</span><span class="sxs-lookup"><span data-stu-id="faba8-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="faba8-114">Ele é usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="faba8-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="faba8-115">Como o tipo de um parâmetro de método no método `AddHead`.</span><span class="sxs-lookup"><span data-stu-id="faba8-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="faba8-116">Como o tipo de retorno da propriedade `Data` na classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="faba8-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="faba8-117">Como o tipo de `data` do membro particular na classe aninhada.</span><span class="sxs-lookup"><span data-stu-id="faba8-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="faba8-118">Observe que T está disponível para a classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="faba8-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="faba8-119">Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.</span><span class="sxs-lookup"><span data-stu-id="faba8-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="faba8-120">O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="faba8-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="faba8-121">Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="faba8-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="faba8-122">Visão geral de genéricos</span><span class="sxs-lookup"><span data-stu-id="faba8-122">Generics Overview</span></span>  
  
- <span data-ttu-id="faba8-123">Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="faba8-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="faba8-124">O uso mais comum de genéricos é para criar classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="faba8-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="faba8-125">A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="faba8-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="faba8-126">Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="faba8-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="faba8-127">Você pode criar suas próprias interfaces genéricas, classes, métodos, eventos e delegados.</span><span class="sxs-lookup"><span data-stu-id="faba8-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="faba8-128">Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.</span><span class="sxs-lookup"><span data-stu-id="faba8-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="faba8-129">Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="faba8-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="faba8-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="faba8-130">Related Sections</span></span>  
 <span data-ttu-id="faba8-131">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="faba8-131">For more information:</span></span>  
  
- [<span data-ttu-id="faba8-132">Parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="faba8-132">Generic Type Parameters</span></span>](./generic-type-parameters.md)  
  
- [<span data-ttu-id="faba8-133">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="faba8-133">Constraints on Type Parameters</span></span>](./constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="faba8-134">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="faba8-134">Generic Classes</span></span>](./generic-classes.md)  
  
- [<span data-ttu-id="faba8-135">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="faba8-135">Generic Interfaces</span></span>](./generic-interfaces.md)  
  
- [<span data-ttu-id="faba8-136">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="faba8-136">Generic Methods</span></span>](./generic-methods.md)  
  
- [<span data-ttu-id="faba8-137">Delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="faba8-137">Generic Delegates</span></span>](./generic-delegates.md)  
  
- [<span data-ttu-id="faba8-138">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="faba8-138">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="faba8-139">Genéricos e reflexão</span><span class="sxs-lookup"><span data-stu-id="faba8-139">Generics and Reflection</span></span>](./generics-and-reflection.md)  
  
- [<span data-ttu-id="faba8-140">Genéricos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="faba8-140">Generics in the Run Time</span></span>](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="faba8-141">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="faba8-141">C# Language Specification</span></span>  
 <span data-ttu-id="faba8-142">Para obter mais informações, consulte a [Especificação da linguagem C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="faba8-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faba8-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faba8-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="faba8-144">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="faba8-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="faba8-145">Tipos</span><span class="sxs-lookup"><span data-stu-id="faba8-145">Types</span></span>](../types/index.md)
- [<span data-ttu-id="faba8-146">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="faba8-146">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="faba8-147">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="faba8-147">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="faba8-148">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="faba8-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
