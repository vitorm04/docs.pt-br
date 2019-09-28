---
title: Coleções genéricas no .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51938dade8ebd1b84010533e04b26cf989ed5f24
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353950"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="108db-102">Coleções genéricas no .NET</span><span class="sxs-lookup"><span data-stu-id="108db-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="108db-103">A biblioteca de classes do .NET fornece várias classes de coleção genérica nos namespaces <xref:System.Collections.Generic> e <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="108db-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="108db-104">Para obter informações detalhadas sobre essas classes, consulte [Tipos de coleção comumente usados](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="108db-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="108db-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="108db-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="108db-106">Muitos dos tipos de coleção genéricos são diretamente análogos aos tipos não genéricos.</span><span class="sxs-lookup"><span data-stu-id="108db-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="108db-107"><xref:System.Collections.Generic.Dictionary%602> é uma versão genérica de <xref:System.Collections.Hashtable>; ele usa a estrutura genérica <xref:System.Collections.Generic.KeyValuePair%602> para enumeração em vez de <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="108db-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="108db-108"><xref:System.Collections.Generic.List%601> é uma versão genérica de <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="108db-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="108db-109">Há classes <xref:System.Collections.Generic.Queue%601> e <xref:System.Collections.Generic.Stack%601> genéricas que correspondem às versões não genéricas.</span><span class="sxs-lookup"><span data-stu-id="108db-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="108db-110">Há versões genéricas e não genéricas de <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="108db-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="108db-111">As duas versões são híbridas de um dicionário e de uma lista.</span><span class="sxs-lookup"><span data-stu-id="108db-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="108db-112">A classe genérica <xref:System.Collections.Generic.SortedDictionary%602> é um dicionário puro e não tem nenhum equivalente não genérico.</span><span class="sxs-lookup"><span data-stu-id="108db-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="108db-113">A classe genérica <xref:System.Collections.Generic.LinkedList%601> é uma verdadeira lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="108db-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="108db-114">Não tem nenhum equivalente não genérico.</span><span class="sxs-lookup"><span data-stu-id="108db-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="108db-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="108db-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="108db-116">A classe genérica <xref:System.Collections.ObjectModel.Collection%601> fornece uma classe base para derivar seus próprios tipos de coleção genérica.</span><span class="sxs-lookup"><span data-stu-id="108db-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="108db-117">A classe <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> fornece uma maneira fácil de produzir uma coleção somente leitura de qualquer tipo que implementa a interface genérica <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="108db-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="108db-118">A classe genérica <xref:System.Collections.ObjectModel.KeyedCollection%602> fornece uma maneira de armazenar objetos que contêm suas próprias chaves.</span><span class="sxs-lookup"><span data-stu-id="108db-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="108db-119">Outros tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="108db-119">Other Generic Types</span></span>  
 <span data-ttu-id="108db-120">A estrutura genérica <xref:System.Nullable%601> permite que você use tipos de valor como se eles pudessem ser atribuídos `null`.</span><span class="sxs-lookup"><span data-stu-id="108db-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="108db-121">Isso pode ser útil ao trabalhar com consultas de banco de dados, nas quais os campos que contêm tipos de valor podem estar ausentes.</span><span class="sxs-lookup"><span data-stu-id="108db-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="108db-122">O parâmetro de tipo genérico pode ser qualquer tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="108db-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="108db-123">No C# e Visual Basic não é necessário usar <xref:System.Nullable%601> explicitamente, pois a linguagem tem sintaxe para tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="108db-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="108db-124">Consulte [tipos de valores anuláveis (guia deC# programação)](../../csharp/programming-guide/nullable-types/index.md) e [tipos de valores anuláveis (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="108db-124">See [Nullable value types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="108db-125">A estrutura genérica <xref:System.ArraySegment%601> fornece uma maneira de delimitar um intervalo de elementos dentro de uma matriz unidimensional baseada em zero de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="108db-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="108db-126">O parâmetro de tipo genérico é o tipo dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="108db-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="108db-127">O delegado genérico <xref:System.EventHandler%601> eliminará a necessidade de declarar um tipo de delegado para manipular eventos, se o evento seguir o padrão de manipulação de eventos usado pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="108db-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="108db-128">Por exemplo, vamos supor que você tenha criado uma classe `MyEventArgs`, derivada de <xref:System.EventArgs>, para manter os dados para o evento.</span><span class="sxs-lookup"><span data-stu-id="108db-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="108db-129">Em seguida, você pode declarar o evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="108db-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="108db-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="108db-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="108db-131">Genéricos</span><span class="sxs-lookup"><span data-stu-id="108db-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="108db-132">Delegados genéricos para manipulação de matrizes e listas</span><span class="sxs-lookup"><span data-stu-id="108db-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="108db-133">Interfaces genéricas</span><span class="sxs-lookup"><span data-stu-id="108db-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
