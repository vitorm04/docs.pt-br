---
title: Classificando dados (C#)
description: Saiba mais sobre operações de classificação e os métodos de operador de consulta padrão que executam operações de classificação em LINQ em C#.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 0665e5dec95fd2929d24d82568de66597df1c0bd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195500"
---
# <a name="sorting-data-c"></a><span data-ttu-id="ee3ca-103">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="ee3ca-103">Sorting Data (C#)</span></span>

<span data-ttu-id="ee3ca-104">Uma operação de classificação ordena os elementos de uma sequência com base em um ou mais atributos.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="ee3ca-105">O primeiro critério de classificação executa uma classificação primária dos elementos.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="ee3ca-106">Especificando um segundo critério de classificação, você pode classificar os elementos dentro de cada grupo de classificação primário.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="ee3ca-107">A ilustração a seguir mostra os resultados de uma operação de classificação alfabética em uma sequência de caracteres:</span><span class="sxs-lookup"><span data-stu-id="ee3ca-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Gráfico que mostra uma operação de classificação alfabética.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="ee3ca-109">Os métodos de operador de consulta padrão que classificam dados estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee3ca-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="ee3ca-110">Methods</span></span>  
  
|<span data-ttu-id="ee3ca-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="ee3ca-111">Method Name</span></span>|<span data-ttu-id="ee3ca-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee3ca-112">Description</span></span>|<span data-ttu-id="ee3ca-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="ee3ca-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="ee3ca-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="ee3ca-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ee3ca-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ee3ca-115">OrderBy</span></span>|<span data-ttu-id="ee3ca-116">Classifica valores em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee3ca-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="ee3ca-117">OrderByDescending</span></span>|<span data-ttu-id="ee3ca-118">Classifica valores em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee3ca-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ee3ca-119">ThenBy</span></span>|<span data-ttu-id="ee3ca-120">Executa uma classificação secundária em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee3ca-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="ee3ca-121">ThenByDescending</span></span>|<span data-ttu-id="ee3ca-122">Executa uma classificação secundária em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ee3ca-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="ee3ca-123">Reverse</span></span>|<span data-ttu-id="ee3ca-124">Inverte a ordem dos elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="ee3ca-125">Não aplicável.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ee3ca-126">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="ee3ca-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="ee3ca-127">Exemplos de classificação primária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="ee3ca-128">Classificação crescente primária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-128">Primary Ascending Sort</span></span>  

 <span data-ttu-id="ee3ca-129">O exemplo a seguir demonstra como usar a cláusula `orderby` em uma consulta de LINQ para classificar as cadeias de caracteres em uma matriz segundo o tamanho da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="ee3ca-130">Classificação decrescente primária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-130">Primary Descending Sort</span></span>  

 <span data-ttu-id="ee3ca-131">O exemplo seguinte demonstra como usar a cláusula `orderby descending` em uma consulta de LINQ para classificar as cadeias de caracteres segundo sua primeira letra, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="ee3ca-132">Exemplos de classificação secundária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="ee3ca-133">Classificação crescente secundária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-133">Secondary Ascending Sort</span></span>  

 <span data-ttu-id="ee3ca-134">O exemplo a seguir demonstra como usar a cláusula `orderby` em uma consulta de LINQ para executar uma classificação primária e uma classificação secundária das cadeias de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="ee3ca-135">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres, em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="ee3ca-136">Classificação decrescente secundária</span><span class="sxs-lookup"><span data-stu-id="ee3ca-136">Secondary Descending Sort</span></span>  

 <span data-ttu-id="ee3ca-137">O exemplo seguinte demonstra como usar a cláusula `orderby descending` em uma consulta de LINQ para executar uma classificação primária, em ordem crescente e uma classificação secundária, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="ee3ca-138">As cadeias de caracteres são classificadas primeiro segundo o tamanho e, depois, segundo a primeira letra da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ee3ca-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee3ca-139">Veja também</span><span class="sxs-lookup"><span data-stu-id="ee3ca-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ee3ca-140">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="ee3ca-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ee3ca-141">Cláusula orderby</span><span class="sxs-lookup"><span data-stu-id="ee3ca-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="ee3ca-142">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="ee3ca-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="ee3ca-143">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ee3ca-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
