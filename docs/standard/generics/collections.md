---
title: "Coleções genéricas no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="a6f5f-102">Coleções genéricas no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a6f5f-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="a6f5f-103">Este tópico fornece uma visão geral das classes de coleção genérica e outros tipos genéricos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="a6f5f-104">Coleções genéricas no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a6f5f-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="a6f5f-105">A biblioteca de classes do .NET Framework fornece um número de classes de coleção genérica de <xref:System.Collections.Generic> e <xref:System.Collections.ObjectModel> namespaces.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="a6f5f-106">Para obter mais informações sobre essas classes, consulte [usado comumente tipos de coleção](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5f-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="a6f5f-107">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="a6f5f-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="a6f5f-108">Muitos dos tipos de coleção genérica são diretamente análogos aos tipos não genérica.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="a6f5f-109"><xref:System.Collections.Generic.Dictionary%602>é uma versão genérica do <xref:System.Collections.Hashtable>; ele usa a estrutura genérica <xref:System.Collections.Generic.KeyValuePair%602> para enumeração em vez de <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="a6f5f-110"><xref:System.Collections.Generic.List%601>é uma versão genérica do <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="a6f5f-111">Há genérico <xref:System.Collections.Generic.Queue%601> e <xref:System.Collections.Generic.Stack%601> classes que correspondem às versões não genéricas.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="a6f5f-112">Há versões genéricas e <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="a6f5f-113">Ambas as versões são híbridas de um dicionário e uma lista.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="a6f5f-114">O <xref:System.Collections.Generic.SortedDictionary%602> classe genérica é um dicionário puro e não tem nenhum equivalente não genérico.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="a6f5f-115">O <xref:System.Collections.Generic.LinkedList%601> classe genérica é uma lista vinculada true.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="a6f5f-116">Ele tem nenhum equivalente não genérico.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="a6f5f-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="a6f5f-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="a6f5f-118">O <xref:System.Collections.ObjectModel.Collection%601> classe genérica fornece uma classe base para derivar seus próprios tipos de coleção genérica.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="a6f5f-119">O <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> classe fornece uma maneira fácil de produzir uma coleção somente leitura de qualquer tipo que implementa o <xref:System.Collections.Generic.IList%601> interface genérica.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="a6f5f-120">O <xref:System.Collections.ObjectModel.KeyedCollection%602> classe genérica fornece uma maneira de armazenar objetos que contêm suas próprias chaves.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="a6f5f-121">Outros tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="a6f5f-121">Other Generic Types</span></span>  
 <span data-ttu-id="a6f5f-122">O <xref:System.Nullable%601> estrutura genérica permite que você use tipos de valor como se eles podem ser atribuídos `null`.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="a6f5f-123">Isso pode ser útil ao trabalhar com consultas de banco de dados, onde os campos que contêm tipos de valor podem estar ausentes.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="a6f5f-124">O parâmetro de tipo genérico pode ser qualquer tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6f5f-125">No c#, não é necessário usar <xref:System.Nullable%601> explicitamente porque a linguagem possui sintaxe para tipos anuláveis.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="a6f5f-126">O <xref:System.ArraySegment%601> estrutura genérica fornece uma maneira de delimitar um intervalo de elementos dentro de uma matriz unidimensional, de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="a6f5f-127">O parâmetro de tipo genérico é o tipo dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="a6f5f-128">O <xref:System.EventHandler%601> delegado genérico elimina a necessidade de declarar um tipo de delegado para manipular eventos, se o evento segue o padrão de manipulação de eventos usado pelo [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6f5f-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="a6f5f-129">Por exemplo, suponha que você tenha criado um `MyEventArgs` classe derivada de <xref:System.EventArgs>, para manter os dados para o evento.</span><span class="sxs-lookup"><span data-stu-id="a6f5f-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="a6f5f-130">Em seguida, você pode declarar o evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a6f5f-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a6f5f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6f5f-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="a6f5f-132">Genéricos</span><span class="sxs-lookup"><span data-stu-id="a6f5f-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="a6f5f-133">Delegados genéricos para manipulação de matrizes e listas</span><span class="sxs-lookup"><span data-stu-id="a6f5f-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="a6f5f-134">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="a6f5f-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
