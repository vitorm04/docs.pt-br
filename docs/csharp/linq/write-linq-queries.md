---
title: Escrever consultas LINQ em C#
description: Como gravar consultas.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7051e33a185b0ab898c4b9d7368f8f0e6883c119
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="write-linq-queries-in-c"></a><span data-ttu-id="d6566-104">Escrever consultas LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="d6566-104">Write LINQ queries in C#</span></span>

<span data-ttu-id="d6566-105">Este tópico mostra as três maneiras em que você pode escrever uma consulta LINQ em C#:</span><span class="sxs-lookup"><span data-stu-id="d6566-105">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="d6566-106">Usar a sintaxe de consulta.</span><span class="sxs-lookup"><span data-stu-id="d6566-106">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="d6566-107">Usar a sintaxe do método.</span><span class="sxs-lookup"><span data-stu-id="d6566-107">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="d6566-108">Usar uma combinação da sintaxe de consulta e da sintaxe de método.</span><span class="sxs-lookup"><span data-stu-id="d6566-108">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="d6566-109">Os exemplos a seguir demonstram algumas consultas LINQ simples usando cada abordagem listada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d6566-109">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="d6566-110">Em geral, a regra é usar (1) sempre que possível e usar (2) e (3) sempre que necessário.</span><span class="sxs-lookup"><span data-stu-id="d6566-110">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6566-111">Essas consultas funcionam em coleções na memória simples, no entanto, a sintaxe básica é idêntica àquela usada no LINQ to Entities e no LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d6566-111">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6566-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6566-112">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="d6566-113">Sintaxe de consulta</span><span class="sxs-lookup"><span data-stu-id="d6566-113">Query syntax</span></span>  
 <span data-ttu-id="d6566-114">A maneira recomendada de escrever a maioria das consultas é usar a *sintaxe de consulta* para criar *expressões de consulta*.</span><span class="sxs-lookup"><span data-stu-id="d6566-114">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="d6566-115">O exemplo a seguir mostra três expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="d6566-115">The following example shows three query expressions.</span></span> <span data-ttu-id="d6566-116">A primeira expressão de consulta demonstra como filtrar ou restringir os resultados aplicando condições com uma cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="d6566-116">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="d6566-117">Ela retorna todos os elementos na sequência de origem cujos valores são maiores que 7 ou menores que 3.</span><span class="sxs-lookup"><span data-stu-id="d6566-117">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="d6566-118">A segunda expressão demonstra como ordenar os resultados retornados.</span><span class="sxs-lookup"><span data-stu-id="d6566-118">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="d6566-119">A terceira expressão demonstra como agrupar resultados de acordo com uma chave.</span><span class="sxs-lookup"><span data-stu-id="d6566-119">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="d6566-120">Esta consulta retorna dois grupos com base na primeira letra da palavra.</span><span class="sxs-lookup"><span data-stu-id="d6566-120">This query returns two groups based on the first letter of the word.</span></span>  
  
 <span data-ttu-id="d6566-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d6566-121">[!code-cs[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]</span></span>  
  
 <span data-ttu-id="d6566-122">Observe que o tipo das consultas é <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d6566-122">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d6566-123">Todas essas consultas poderiam ser escritas usando `var` conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6566-123">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="d6566-124">Em cada exemplo anterior, as consultas não são de fato executadas até você iterar na variável de consulta em uma instrução `foreach` ou outra instrução.</span><span class="sxs-lookup"><span data-stu-id="d6566-124">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="d6566-125">Para obter mais informações, consulte [Introdução a Consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d6566-125">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6566-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6566-126">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="d6566-127">Sintaxe do método</span><span class="sxs-lookup"><span data-stu-id="d6566-127">Method syntax</span></span>  
 <span data-ttu-id="d6566-128">Algumas operações de consulta devem ser expressas como uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="d6566-128">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="d6566-129">Os mais comuns desses métodos são aqueles que retornam valores numéricos singleton como <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A> e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="d6566-129">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="d6566-130">Esses métodos devem sempre ser chamados por último em qualquer consulta porque representam apenas um único valor e não podem atuar como a fonte para uma operação de consulta adicional.</span><span class="sxs-lookup"><span data-stu-id="d6566-130">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="d6566-131">O exemplo a seguir mostra uma chamada de método em uma expressão de consulta:</span><span class="sxs-lookup"><span data-stu-id="d6566-131">The following example shows a method call in a query expression:</span></span>  
  
 <span data-ttu-id="d6566-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d6566-132">[!code-cs[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6566-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6566-133">Example</span></span>  
 <span data-ttu-id="d6566-134">Se o método tiver os parâmetros Action ou Func, eles serão fornecidos na forma de uma expressão [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md), como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6566-134">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 <span data-ttu-id="d6566-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d6566-135">[!code-cs[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]</span></span>  
  
 <span data-ttu-id="d6566-136">Nas consultas anteriores, apenas a Query #4 é executada imediatamente.</span><span class="sxs-lookup"><span data-stu-id="d6566-136">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="d6566-137">Isso ocorre porque ele retorna um único valor e não uma coleção <xref:System.Collections.Generic.IEnumerable%601> genérica.</span><span class="sxs-lookup"><span data-stu-id="d6566-137">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="d6566-138">O próprio método tem que usar `foreach` para calcular seu valor.</span><span class="sxs-lookup"><span data-stu-id="d6566-138">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="d6566-139">Cada uma das consultas anteriores pode ser escrita usando a tipagem implícita com [var](../language-reference/keywords/var.md), como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d6566-139">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 <span data-ttu-id="d6566-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d6566-140">[!code-cs[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6566-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6566-141">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="d6566-142">Sintaxe de consulta e do método mista</span><span class="sxs-lookup"><span data-stu-id="d6566-142">Mixed query and method syntax</span></span>  
 <span data-ttu-id="d6566-143">Este exemplo mostra como usar a sintaxe do método nos resultados de uma cláusula de consulta.</span><span class="sxs-lookup"><span data-stu-id="d6566-143">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="d6566-144">Simplesmente coloque a expressão de consulta entre parênteses e, em seguida, aplique o operador de ponto e chame o método.</span><span class="sxs-lookup"><span data-stu-id="d6566-144">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="d6566-145">No exemplo a seguir, a Query #7 retorna uma contagem dos números cujo valor está entre 3 e 7.</span><span class="sxs-lookup"><span data-stu-id="d6566-145">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="d6566-146">Em geral, no entanto, é melhor usar uma segunda variável para armazenar o resultado da chamada do método.</span><span class="sxs-lookup"><span data-stu-id="d6566-146">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="d6566-147">Dessa forma, é menos provável que a consulta seja confundida com os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="d6566-147">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 <span data-ttu-id="d6566-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d6566-148">[!code-cs[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]</span></span>  
  
 <span data-ttu-id="d6566-149">Como a Query #7 retorna um único valor e não uma coleção, a consulta é executada imediatamente.</span><span class="sxs-lookup"><span data-stu-id="d6566-149">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="d6566-150">A consulta anterior pode ser escrita usando a tipagem implícita com `var`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d6566-150">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="d6566-151">Ela pode ser escrita na sintaxe de método da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d6566-151">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="d6566-152">Ela pode ser escrita usando a tipagem explícita da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d6566-152">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6566-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6566-153">See Also</span></span>  
  <span data-ttu-id="d6566-154">[Passo a passo: escrevendo consultas em C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d6566-154">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 <span data-ttu-id="d6566-155">[Expressões de Consulta LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="d6566-155">[LINQ Query Expressions](index.md) </span></span>  
 [<span data-ttu-id="d6566-156">Cláusula where</span><span class="sxs-lookup"><span data-stu-id="d6566-156">where clause</span></span>](../language-reference/keywords/where-clause.md)

