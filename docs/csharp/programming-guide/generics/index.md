---
title: Genéricos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 4ff0dd872e1b09e993c947f008c964ad204ad09a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039353"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="26a59-102">Genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="26a59-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="26a59-103">Os genéricos apresentam o conceito de parâmetros de tipo para o .NET Framework, o que possibilita criar classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou o método seja declarado e instanciado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="26a59-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="26a59-104">Por exemplo, usando um parâmetro de tipo genérico `T`, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer no custo ou risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="26a59-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="26a59-105">Classes e métodos genéricos combinam reusabilidade, segurança de tipo e eficiência de forma que suas contrapartes não genéricas não possam.</span><span class="sxs-lookup"><span data-stu-id="26a59-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="26a59-106">Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas.</span><span class="sxs-lookup"><span data-stu-id="26a59-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="26a59-107">O namespace <xref:System.Collections.Generic> contém várias classes de coleção baseadas em genéricos.</span><span class="sxs-lookup"><span data-stu-id="26a59-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="26a59-108">As coleções não genéricas, como <xref:System.Collections.ArrayList> não são recomendadas e são mantidas para fins de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="26a59-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="26a59-109">Para saber mais, confira [Genéricos no .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="26a59-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="26a59-110">É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes.</span><span class="sxs-lookup"><span data-stu-id="26a59-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="26a59-111">O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="26a59-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="26a59-112">(Na maioria dos casos, você deve usar a classe <xref:System.Collections.Generic.List%601> fornecida pela .NET Framework biblioteca de classes em vez de criar a sua própria.) O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista.</span><span class="sxs-lookup"><span data-stu-id="26a59-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="26a59-113">Ele é usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="26a59-113">It is used in the following ways:</span></span>

- <span data-ttu-id="26a59-114">Como o tipo de um parâmetro de método no método `AddHead`.</span><span class="sxs-lookup"><span data-stu-id="26a59-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="26a59-115">Como o tipo de retorno da propriedade `Data` na classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="26a59-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="26a59-116">Como o tipo de `data` do membro particular na classe aninhada.</span><span class="sxs-lookup"><span data-stu-id="26a59-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="26a59-117">Observe que `T` está disponível para a classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="26a59-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="26a59-118">Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.</span><span class="sxs-lookup"><span data-stu-id="26a59-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)] 

<span data-ttu-id="26a59-119">O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="26a59-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="26a59-120">Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="26a59-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="26a59-121">Visão geral dos genéricos</span><span class="sxs-lookup"><span data-stu-id="26a59-121">Generics overview</span></span>

- <span data-ttu-id="26a59-122">Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.</span><span class="sxs-lookup"><span data-stu-id="26a59-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="26a59-123">O uso mais comum de genéricos é para criar classes de coleção.</span><span class="sxs-lookup"><span data-stu-id="26a59-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="26a59-124">A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="26a59-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="26a59-125">Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="26a59-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="26a59-126">Você pode criar suas próprias interfaces, classes, métodos, eventos e delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="26a59-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="26a59-127">Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.</span><span class="sxs-lookup"><span data-stu-id="26a59-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="26a59-128">Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.</span><span class="sxs-lookup"><span data-stu-id="26a59-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="26a59-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="26a59-129">Related sections</span></span>

- [<span data-ttu-id="26a59-130">Parâmetros de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="26a59-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="26a59-131">Restrições a parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="26a59-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="26a59-132">Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="26a59-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="26a59-133">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="26a59-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="26a59-134">Métodos genéricos</span><span class="sxs-lookup"><span data-stu-id="26a59-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="26a59-135">Delegados genéricos</span><span class="sxs-lookup"><span data-stu-id="26a59-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="26a59-136">Diferenças entre modelos C++ e genéricos C#</span><span class="sxs-lookup"><span data-stu-id="26a59-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="26a59-137">Genéricos e reflexão</span><span class="sxs-lookup"><span data-stu-id="26a59-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="26a59-138">Genéricos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="26a59-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="26a59-139">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="26a59-139">C# language specification</span></span>

<span data-ttu-id="26a59-140">Para obter mais informações, consulte a [Especificação da linguagem C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="26a59-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="26a59-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26a59-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="26a59-142">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="26a59-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="26a59-143">Tipos</span><span class="sxs-lookup"><span data-stu-id="26a59-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="26a59-144">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="26a59-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="26a59-145">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="26a59-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="26a59-146">Genéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="26a59-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
