---
title: Executar operações de junção personalizadas (LINQ em C#)
description: Saiba como executar operações de junção personalizadas de LINQ em C#.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44217419"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="35ad1-103">Executar operações de junção personalizadas</span><span class="sxs-lookup"><span data-stu-id="35ad1-103">Perform custom join operations</span></span>

<span data-ttu-id="35ad1-104">Este exemplo mostra como executar operações de junção que não são possíveis com a cláusula `join`.</span><span class="sxs-lookup"><span data-stu-id="35ad1-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="35ad1-105">Em uma expressão de consulta, a cláusula `join` é limitada e otimizada para junções por igualdade, que são, de longe, o tipo de operação de junção mais comum.</span><span class="sxs-lookup"><span data-stu-id="35ad1-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="35ad1-106">Ao realizar uma junção por igualdade, provavelmente você terá o melhor desempenho usando a cláusula `join`.</span><span class="sxs-lookup"><span data-stu-id="35ad1-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="35ad1-107">No entanto, a cláusula `join` não pode ser usada nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="35ad1-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="35ad1-108">Quando a junção se baseia em uma expressão de desigualdade (uma junção que não é por igualdade).</span><span class="sxs-lookup"><span data-stu-id="35ad1-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="35ad1-109">Quando a junção se baseia em mais de uma expressão de igualdade ou desigualdade.</span><span class="sxs-lookup"><span data-stu-id="35ad1-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="35ad1-110">Quando for necessário introduzir uma variável de intervalo temporária para a sequência do lado direito (interna) antes da operação de junção.</span><span class="sxs-lookup"><span data-stu-id="35ad1-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="35ad1-111">Para executar junções que não são junções por igualdade, você pode usar várias cláusulas `from` para introduzir cada fonte de dados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="35ad1-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="35ad1-112">Em seguida, você aplica uma expressão de predicado em uma cláusula `where` à variável de intervalo para cada fonte.</span><span class="sxs-lookup"><span data-stu-id="35ad1-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="35ad1-113">A expressão também pode assumir a forma de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="35ad1-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="35ad1-114">Não confunda esse tipo de operação de junção personalizada com o uso de várias cláusulas `from` para acessar coleções internas.</span><span class="sxs-lookup"><span data-stu-id="35ad1-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="35ad1-115">Para obter mais informações, consulte [Cláusula join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="35ad1-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="35ad1-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35ad1-116">Example</span></span>

<span data-ttu-id="35ad1-117">O primeiro método no exemplo a seguir mostra uma união cruzada simples.</span><span class="sxs-lookup"><span data-stu-id="35ad1-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="35ad1-118">Uniões cruzadas devem ser usadas com cuidado porque podem produzir conjuntos de resultados muito grandes.</span><span class="sxs-lookup"><span data-stu-id="35ad1-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="35ad1-119">No entanto, elas podem ser úteis em alguns cenários para criar sequências de origem em que são executadas consultas adicionais.</span><span class="sxs-lookup"><span data-stu-id="35ad1-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="35ad1-120">O segundo método produz uma sequência de todos os produtos cuja ID da categoria está na lista de categorias no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="35ad1-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="35ad1-121">Observe o uso da cláusula `let` e do método `Contains` para criar uma matriz temporária.</span><span class="sxs-lookup"><span data-stu-id="35ad1-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="35ad1-122">Também é possível criar a matriz antes da consulta e eliminar a primeira cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="35ad1-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="35ad1-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35ad1-123">Example</span></span>

<span data-ttu-id="35ad1-124">No exemplo a seguir, a consulta deve unir duas sequências com base nas chaves correspondentes que, no caso da sequência interna (lado direito), não podem ser obtidas antes da cláusula join.</span><span class="sxs-lookup"><span data-stu-id="35ad1-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="35ad1-125">Se essa junção tiver sido executada com uma cláusula `join`, o método `Split` precisará ser chamado para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="35ad1-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="35ad1-126">O uso de várias cláusulas `from` permite que a consulta evite a sobrecarga da chamada de método repetida.</span><span class="sxs-lookup"><span data-stu-id="35ad1-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="35ad1-127">No entanto, como `join` é otimizado, neste caso em particular ainda pode ser mais rápido do que usar várias cláusulas `from`.</span><span class="sxs-lookup"><span data-stu-id="35ad1-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="35ad1-128">Os resultados variam dependendo principalmente do quanto a chamada de método é cara.</span><span class="sxs-lookup"><span data-stu-id="35ad1-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="35ad1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35ad1-129">See also</span></span>

- [<span data-ttu-id="35ad1-130">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="35ad1-130">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="35ad1-131">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="35ad1-131">join clause</span></span>](../language-reference/keywords/join-clause.md)  
- [<span data-ttu-id="35ad1-132">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="35ad1-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)  