---
title: Escrever consultas LINQ em C#
description: Saiba como escrever consultas LINQ em C#.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 2ebba0d2d601932c976a88726fbe3ed37daffdcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463098"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="45339-103">Escrever consultas LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="45339-103">Write LINQ queries in C#</span></span> #

<span data-ttu-id="45339-104">Este artigo mostra as três maneiras de escrever uma consulta LINQ em C#:</span><span class="sxs-lookup"><span data-stu-id="45339-104">This article shows the three ways in which you can write a LINQ query in C#:</span></span>

1. <span data-ttu-id="45339-105">Usar a sintaxe de consulta.</span><span class="sxs-lookup"><span data-stu-id="45339-105">Use query syntax.</span></span>

2. <span data-ttu-id="45339-106">Usar a sintaxe do método.</span><span class="sxs-lookup"><span data-stu-id="45339-106">Use method syntax.</span></span>

3. <span data-ttu-id="45339-107">Usar uma combinação da sintaxe de consulta e da sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="45339-107">Use a combination of query syntax and method syntax.</span></span>

<span data-ttu-id="45339-108">Os exemplos a seguir demonstram algumas consultas LINQ simples usando cada abordagem listada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="45339-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="45339-109">Em geral, a regra é usar (1) sempre que possível e usar (2) e (3) sempre que necessário.</span><span class="sxs-lookup"><span data-stu-id="45339-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="45339-110">Essas consultas funcionam em coleções na memória simples, no entanto, a sintaxe básica é idêntica àquela usada no LINQ to Entities e no LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="45339-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>

## <a name="example---query-syntax"></a><span data-ttu-id="45339-111">Exemplo – sintaxe de consulta</span><span class="sxs-lookup"><span data-stu-id="45339-111">Example - Query syntax</span></span>

<span data-ttu-id="45339-112">A maneira recomendada de escrever a maioria das consultas é usar a *sintaxe de consulta* para criar *expressões de consulta*.</span><span class="sxs-lookup"><span data-stu-id="45339-112">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="45339-113">O exemplo a seguir mostra três expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="45339-113">The following example shows three query expressions.</span></span> <span data-ttu-id="45339-114">A primeira expressão de consulta demonstra como filtrar ou restringir os resultados aplicando condições com uma cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="45339-114">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="45339-115">Ela retorna todos os elementos na sequência de origem cujos valores são maiores que 7 ou menores que 3.</span><span class="sxs-lookup"><span data-stu-id="45339-115">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="45339-116">A segunda expressão demonstra como ordenar os resultados retornados.</span><span class="sxs-lookup"><span data-stu-id="45339-116">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="45339-117">A terceira expressão demonstra como agrupar resultados de acordo com uma chave.</span><span class="sxs-lookup"><span data-stu-id="45339-117">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="45339-118">Esta consulta retorna dois grupos com base na primeira letra da palavra.</span><span class="sxs-lookup"><span data-stu-id="45339-118">This query returns two groups based on the first letter of the word.</span></span>

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

<span data-ttu-id="45339-119">Observe que o tipo das consultas é <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="45339-119">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="45339-120">Todas essas consultas poderiam ser escritas usando `var` conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="45339-120">All of these queries could be written using `var` as shown in the following example:</span></span>

`var query = from num in numbers...`

<span data-ttu-id="45339-121">Em cada exemplo anterior, as consultas não são de fato executadas até você iterar na variável de consulta em uma instrução `foreach` ou outra instrução.</span><span class="sxs-lookup"><span data-stu-id="45339-121">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="45339-122">Para obter mais informações, consulte [Introdução a Consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="45339-122">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="example---method-syntax"></a><span data-ttu-id="45339-123">Exemplo – sintaxe de método</span><span class="sxs-lookup"><span data-stu-id="45339-123">Example - Method syntax</span></span>

<span data-ttu-id="45339-124">Algumas operações de consulta devem ser expressas como uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="45339-124">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="45339-125">Os mais comuns desses métodos são aqueles que retornam valores numéricos singleton como <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A> e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="45339-125">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="45339-126">Esses métodos devem sempre ser chamados por último em qualquer consulta porque representam apenas um único valor e não podem atuar como a fonte para uma operação de consulta adicional.</span><span class="sxs-lookup"><span data-stu-id="45339-126">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="45339-127">O exemplo a seguir mostra uma chamada de método em uma expressão de consulta:</span><span class="sxs-lookup"><span data-stu-id="45339-127">The following example shows a method call in a query expression:</span></span>

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

<span data-ttu-id="45339-128">Se o método tiver os parâmetros Action ou Func, eles serão fornecidos na forma de uma expressão [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md), como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="45339-128">If the method has Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

<span data-ttu-id="45339-129">Nas consultas anteriores, apenas a Query #4 é executada imediatamente.</span><span class="sxs-lookup"><span data-stu-id="45339-129">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="45339-130">Isso ocorre porque ele retorna um único valor e não uma coleção <xref:System.Collections.Generic.IEnumerable%601> genérica.</span><span class="sxs-lookup"><span data-stu-id="45339-130">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="45339-131">O próprio método tem que usar `foreach` para calcular seu valor.</span><span class="sxs-lookup"><span data-stu-id="45339-131">The method itself has to use `foreach` in order to compute its value.</span></span>

<span data-ttu-id="45339-132">Cada uma das consultas anteriores pode ser escrita usando a tipagem implícita com [var](../language-reference/keywords/var.md), como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="45339-132">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a><span data-ttu-id="45339-133">Exemplo – sintaxe mista de consulta e do método</span><span class="sxs-lookup"><span data-stu-id="45339-133">Example - Mixed query and method syntax</span></span>

<span data-ttu-id="45339-134">Este exemplo mostra como usar a sintaxe do método nos resultados de uma cláusula de consulta.</span><span class="sxs-lookup"><span data-stu-id="45339-134">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="45339-135">Simplesmente coloque a expressão de consulta entre parênteses e, em seguida, aplique o operador de ponto e chame o método.</span><span class="sxs-lookup"><span data-stu-id="45339-135">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="45339-136">No exemplo a seguir, a Query #7 retorna uma contagem dos números cujo valor está entre 3 e 7.</span><span class="sxs-lookup"><span data-stu-id="45339-136">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="45339-137">Em geral, no entanto, é melhor usar uma segunda variável para armazenar o resultado da chamada do método.</span><span class="sxs-lookup"><span data-stu-id="45339-137">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="45339-138">Dessa forma, é menos provável que a consulta seja confundida com os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="45339-138">In this manner, the query is less likely to be confused with the results of the query.</span></span>

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

<span data-ttu-id="45339-139">Como a Query #7 retorna um único valor e não uma coleção, a consulta é executada imediatamente.</span><span class="sxs-lookup"><span data-stu-id="45339-139">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>

<span data-ttu-id="45339-140">A consulta anterior pode ser escrita usando a tipagem implícita com `var`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="45339-140">The previous query can be written by using implicit typing with `var`, as follows:</span></span>

```csharp
var numCount = (from num in numbers...
```

<span data-ttu-id="45339-141">Ela pode ser escrita na sintaxe de método da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="45339-141">It can be written in method syntax as follows:</span></span>

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

<span data-ttu-id="45339-142">Ela pode ser escrita usando a tipagem explícita da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="45339-142">It can be written by using explicit typing, as follows:</span></span>

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a><span data-ttu-id="45339-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45339-143">See also</span></span>

- [<span data-ttu-id="45339-144">Passo a passo: escrevendo consultas em C#</span><span class="sxs-lookup"><span data-stu-id="45339-144">Walkthrough: Writing Queries in C#</span></span>](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="45339-145">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="45339-145">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="45339-146">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="45339-146">where clause</span></span>](../language-reference/keywords/where-clause.md)