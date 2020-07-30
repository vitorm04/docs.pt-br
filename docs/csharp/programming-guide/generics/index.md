---
title: Genéricos – Guia de Programação em C#
description: Saiba mais sobre os genéricos. Os tipos genéricos maximizam a reutilização de código, a segurança de tipo e o desempenho, e são comumente usados para criar classes de coleção.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: beef9c20e3ac62505bc7a4584b404637935de1dc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299390"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="48b8a-104">Genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="48b8a-104">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="48b8a-105">Os genéricos apresentam o conceito de parâmetros de tipo para .NET, o que possibilita criar classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou o método seja declarado e instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="48b8a-105">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="48b8a-106">Por exemplo, usando um parâmetro de tipo genérico `T` , você pode escrever uma única classe que outro código de cliente pode usar sem incorrer no custo ou risco de conversões de tempo de execução ou operações boxing, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="48b8a-106">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="48b8a-107">Classes e métodos genéricos combinam reusabilidade, segurança de tipo e eficiência de forma que suas contrapartes não genéricas não possam.</span><span class="sxs-lookup"><span data-stu-id="48b8a-107">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="48b8a-108">Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas.</span><span class="sxs-lookup"><span data-stu-id="48b8a-108">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="48b8a-109">O <xref:System.Collections.Generic> namespace contém várias classes de coleção baseadas em genéricos.</span><span class="sxs-lookup"><span data-stu-id="48b8a-109">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="48b8a-110">As coleções não genéricas, como <xref:System.Collections.ArrayList> não são recomendadas e são mantidas para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="48b8a-110">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="48b8a-111">Para saber mais, confira [Genéricos no .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="48b8a-111">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="48b8a-112">É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes.</span><span class="sxs-lookup"><span data-stu-id="48b8a-112">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="48b8a-113">O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="48b8a-113">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="48b8a-114">(Na maioria dos casos, você deve usar a <xref:System.Collections.Generic.List%601> classe fornecida pelo .net em vez de criar a sua própria.) O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista.</span><span class="sxs-lookup"><span data-stu-id="48b8a-114">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="48b8a-115">Ele é usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="48b8a-115">It is used in the following ways:</span></span>

- <span data-ttu-id="48b8a-116">Como o tipo de um parâmetro de método no método `AddHead`.</span><span class="sxs-lookup"><span data-stu-id="48b8a-116">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="48b8a-117">Como o tipo de retorno da propriedade `Data` na classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="48b8a-117">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="48b8a-118">Como o tipo de `data` do membro particular na classe aninhada.</span><span class="sxs-lookup"><span data-stu-id="48b8a-118">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="48b8a-119">Observe que `T` está disponível para a classe aninhada `Node` .</span><span class="sxs-lookup"><span data-stu-id="48b8a-119">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="48b8a-120">Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.</span><span class="sxs-lookup"><span data-stu-id="48b8a-120">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="48b8a-121">O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="48b8a-121">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="48b8a-122">Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="48b8a-122">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="48b8a-123">Visão geral dos genéricos</span><span class="sxs-lookup"><span data-stu-id="48b8a-123">Generics overview</span></span>

- <span data-ttu-id="48b8a-124">Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="48b8a-124">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="48b8a-125">O uso mais comum de genéricos é para criar classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="48b8a-125">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="48b8a-126">A biblioteca de classes .NET contém várias classes de coleção genéricas no <xref:System.Collections.Generic> namespace.</span><span class="sxs-lookup"><span data-stu-id="48b8a-126">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="48b8a-127">Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="48b8a-127">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="48b8a-128">Você pode criar suas próprias interfaces, classes, métodos, eventos e delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="48b8a-128">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="48b8a-129">Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.</span><span class="sxs-lookup"><span data-stu-id="48b8a-129">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="48b8a-130">Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="48b8a-130">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="48b8a-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="48b8a-131">Related sections</span></span>

- [<span data-ttu-id="48b8a-132">Parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="48b8a-132">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="48b8a-133">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="48b8a-133">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="48b8a-134">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="48b8a-134">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="48b8a-135">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="48b8a-135">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="48b8a-136">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="48b8a-136">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="48b8a-137">Delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="48b8a-137">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="48b8a-138">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="48b8a-138">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="48b8a-139">Genéricos e reflexão</span><span class="sxs-lookup"><span data-stu-id="48b8a-139">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="48b8a-140">Genéricos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="48b8a-140">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="48b8a-141">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="48b8a-141">C# language specification</span></span>

<span data-ttu-id="48b8a-142">Para obter mais informações, consulte a [especificação da linguagem C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="48b8a-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="48b8a-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="48b8a-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="48b8a-144">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="48b8a-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="48b8a-145">Types</span><span class="sxs-lookup"><span data-stu-id="48b8a-145">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="48b8a-146">Generics in .NET (Genéricos no .NET)</span><span class="sxs-lookup"><span data-stu-id="48b8a-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
