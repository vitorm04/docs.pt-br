---
title: "Executar junções agrupadas"
description: "Como realizar junções agrupadas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0410c5f673e61f91c00a69cb1659e0d72852f128
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="perform-grouped-joins"></a><span data-ttu-id="f3f15-104">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="f3f15-104">Perform grouped joins</span></span>

<span data-ttu-id="f3f15-105">A junção de grupo é útil para a produção de estruturas de dados hierárquicos.</span><span class="sxs-lookup"><span data-stu-id="f3f15-105">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="f3f15-106">Ela combina cada elemento da primeira coleção com um conjunto de elementos correlacionados da segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="f3f15-106">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="f3f15-107">Por exemplo, uma classe ou uma tabela de banco de dados relacional chamada `Student` pode conter dois campos: `Id` e `Name`.</span><span class="sxs-lookup"><span data-stu-id="f3f15-107">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="f3f15-108">Uma segunda classe ou tabela de banco de dados relacional chamada `Course` pode conter dois campos: `StudentId` e `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="f3f15-108">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="f3f15-109">Uma junção de grupo dessas duas fontes de dados, com base na correspondência de `Student.Id` e `Course.StudentId`, agruparia cada `Student` com uma coleção de objetos `Course` (que pode estar vazia).</span><span class="sxs-lookup"><span data-stu-id="f3f15-109">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3f15-110">Cada elemento da primeira coleção aparece no conjunto de resultados de uma junção de grupo, independentemente de se os elementos correlacionados encontram-se na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="f3f15-110">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="f3f15-111">Caso nenhum elemento correlacionado seja encontrado, a sequência de elementos correlacionados desse elemento ficará vazia.</span><span class="sxs-lookup"><span data-stu-id="f3f15-111">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="f3f15-112">O seletor de resultado, portanto, tem acesso a todos os elementos da primeira coleção.</span><span class="sxs-lookup"><span data-stu-id="f3f15-112">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="f3f15-113">Isso difere do seletor de resultado de uma junção que não é de grupo, que não pode acessar os elementos da primeira coleção que não têm correspondência na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="f3f15-113">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="f3f15-114">O primeiro exemplo deste tópico mostra como realizar uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="f3f15-114">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="f3f15-115">O segundo exemplo mostra como usar uma junção de grupo para criar elementos XML.</span><span class="sxs-lookup"><span data-stu-id="f3f15-115">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f15-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3f15-116">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="f3f15-117">Exemplo de junção de grupo</span><span class="sxs-lookup"><span data-stu-id="f3f15-117">Group join example</span></span>  
 <span data-ttu-id="f3f15-118">O exemplo a seguir realiza uma junção de grupo de objetos do tipo `Person` e `Pet` com base em `Person` correspondente à propriedade `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="f3f15-118">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="f3f15-119">Ao contrário de uma junção que não é de grupo, que produziria um par de elementos para cada correspondência, a junção de grupo produz apenas um objeto resultante para cada elemento da primeira coleção, que neste exemplo é um objeto `Person`.</span><span class="sxs-lookup"><span data-stu-id="f3f15-119">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="f3f15-120">Os elementos correspondentes da segunda coleção, que neste exemplo são objetos `Pet`, são agrupados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="f3f15-120">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="f3f15-121">Por fim, a função de seletor de resultado cria um tipo anônimo para cada correspondência que consiste em `Person.FirstName` e em uma coleção de objetos `Pet`.</span><span class="sxs-lookup"><span data-stu-id="f3f15-121">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 <span data-ttu-id="f3f15-122">[!code-cs[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f15-122">[!code-cs[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f15-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3f15-123">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="f3f15-124">Junção de grupo para criar um exemplo de XML</span><span class="sxs-lookup"><span data-stu-id="f3f15-124">Group join to create XML example</span></span>  
 <span data-ttu-id="f3f15-125">As junções de grupo são ideais para a criação de XML usando o LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="f3f15-125">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="f3f15-126">O exemplo a seguir é semelhante ao exemplo anterior, exceto que em vez de criar tipos anônimos, a função de seletor de resultado cria elementos XML que representam os objetos associados.</span><span class="sxs-lookup"><span data-stu-id="f3f15-126">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 <span data-ttu-id="f3f15-127">[!code-cs[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f15-127">[!code-cs[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="f3f15-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3f15-128">See also</span></span>  
 <span data-ttu-id="f3f15-129"><xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="f3f15-129"><xref:System.Linq.Enumerable.Join%2A></span></span>   
 <span data-ttu-id="f3f15-130"><xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="f3f15-130"><xref:System.Linq.Enumerable.GroupJoin%2A></span></span>   
 <span data-ttu-id="f3f15-131">[Executar junções internas](perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="f3f15-131">[Perform inner joins](perform-inner-joins.md) </span></span>  
 <span data-ttu-id="f3f15-132">[Executar junções externas esquerdas](perform-left-outer-joins.md) </span><span class="sxs-lookup"><span data-stu-id="f3f15-132">[Perform left outer joins](perform-left-outer-joins.md) </span></span>  
 [<span data-ttu-id="f3f15-133">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="f3f15-133">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)   
 

