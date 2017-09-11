---
title: "Executar operações de junção personalizadas"
description: "Como executar operações de junção personalizadas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 51bdae75346022a7564fdb50e582c143e7762a1f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="cc1eb-104">Executar operações de junção personalizadas</span><span class="sxs-lookup"><span data-stu-id="cc1eb-104">Perform custom join operations</span></span>

<span data-ttu-id="cc1eb-105">Este exemplo mostra como executar operações de junção que não são possíveis com a cláusula `join`.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="cc1eb-106">Em uma expressão de consulta, a cláusula `join` é limitada e otimizada para junções por igualdade, que são, de longe, o tipo de operação de junção mais comum.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="cc1eb-107">Ao realizar uma junção por igualdade, provavelmente você terá o melhor desempenho usando a cláusula `join`.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="cc1eb-108">No entanto, a cláusula `join` não pode ser usada nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="cc1eb-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="cc1eb-109">Quando a junção se baseia em uma expressão de desigualdade (uma junção que não é por igualdade).</span><span class="sxs-lookup"><span data-stu-id="cc1eb-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="cc1eb-110">Quando a junção se baseia em mais de uma expressão de igualdade ou desigualdade.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="cc1eb-111">Quando for necessário introduzir uma variável de intervalo temporária para a sequência do lado direito (interna) antes da operação de junção.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="cc1eb-112">Para executar junções que não são equivalentes, você pode usar várias cláusulas `from` para introduzir cada fonte de dados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="cc1eb-113">Em seguida, você aplica uma expressão de predicado em uma cláusula `where` à variável de intervalo para cada fonte.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="cc1eb-114">A expressão também pode assumir a forma de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc1eb-115">Não confunda esse tipo de operação de junção personalizada com o uso de várias cláusulas `from` para acessar coleções internas.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="cc1eb-116">Para obter mais informações, consulte [Cláusula join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cc1eb-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1eb-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc1eb-117">Example</span></span>  
 <span data-ttu-id="cc1eb-118">O primeiro método no exemplo a seguir mostra uma união cruzada simples.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="cc1eb-119">Uniões cruzadas devem ser usadas com cuidado porque podem produzir conjuntos de resultados muito grandes.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="cc1eb-120">No entanto, elas podem ser úteis em alguns cenários para criar sequências de origem em que são executadas consultas adicionais.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="cc1eb-121">O segundo método produz uma sequência de todos os produtos cuja ID da categoria está na lista de categorias no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="cc1eb-122">Observe o uso da cláusula `let` e do método `Contains` para criar uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="cc1eb-123">Também é possível criar a matriz antes da consulta e eliminar a primeira cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 <span data-ttu-id="cc1eb-124">[!code-cs[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cc1eb-124">[!code-cs[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1eb-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc1eb-125">Example</span></span>  
 <span data-ttu-id="cc1eb-126">No exemplo a seguir, a consulta deve unir duas sequências com base nas chaves correspondentes que, no caso da sequência interna (lado direito), não podem ser obtidas antes da cláusula join.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-126">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="cc1eb-127">Se essa junção tiver sido executada com uma cláusula `join`, o método `Split` precisará ser chamado para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-127">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="cc1eb-128">O uso de várias cláusulas `from` permite que a consulta evite a sobrecarga da chamada de método repetida.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-128">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="cc1eb-129">No entanto, como `join` é otimizado, neste caso em particular ainda pode ser mais rápido do que usar várias cláusulas `from`.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-129">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="cc1eb-130">Os resultados variam dependendo principalmente do quanto a chamada de método é cara.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-130">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 <span data-ttu-id="cc1eb-131">[!code-cs[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cc1eb-131">[!code-cs[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1eb-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc1eb-132">See also</span></span>  
 <span data-ttu-id="cc1eb-133">[Expressões de consulta LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="cc1eb-133">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="cc1eb-134">[Cláusula join](../language-reference/keywords/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="cc1eb-134">[join clause](../language-reference/keywords/join-clause.md) </span></span>  
 [<span data-ttu-id="cc1eb-135">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="cc1eb-135">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)

