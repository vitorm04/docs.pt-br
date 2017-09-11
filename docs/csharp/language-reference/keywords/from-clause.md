---
title: "Cláusula from (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- from_CSharpKeyword
- from
dev_langs:
- CSharp
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0165144acfa8d0928015e8222179f7e69f19644
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="from-clause-c-reference"></a><span data-ttu-id="8658c-102">Cláusula from (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8658c-102">from clause (C# Reference)</span></span>
<span data-ttu-id="8658c-103">Uma expressão de consulta deve começar com uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="8658c-103">A query expression must begin with a `from` clause.</span></span> <span data-ttu-id="8658c-104">Além disso, uma expressão de consulta pode conter subconsultas, que também começam com uma cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="8658c-104">Additionally, a query expression can contain sub-queries, which also begin with a `from` clause.</span></span> <span data-ttu-id="8658c-105">A cláusula `from` especifica o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8658c-105">The `from` clause specifies the following:</span></span>  
  
-   <span data-ttu-id="8658c-106">A fonte de dados na qual a consulta ou subconsulta será executada.</span><span class="sxs-lookup"><span data-stu-id="8658c-106">The data source on which the query or sub-query will be run.</span></span>  
  
-   <span data-ttu-id="8658c-107">Uma *variável de intervalo* local que representa cada elemento na sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="8658c-107">A local *range variable* that represents each element in the source sequence.</span></span>  
  
 <span data-ttu-id="8658c-108">A variável de intervalo e a fonte de dados são fortemente tipadas.</span><span class="sxs-lookup"><span data-stu-id="8658c-108">Both the range variable and the data source are strongly typed.</span></span> <span data-ttu-id="8658c-109">A fonte de dados referenciada na cláusula `from` deve ter um tipo de <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> ou um tipo derivado, por exemplo, <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="8658c-109">The data source referenced in the `from` clause must have a type of <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span>  
  
 <span data-ttu-id="8658c-110">No exemplo a seguir, `numbers` é a fonte de dados e `num` é a variável de intervalo.</span><span class="sxs-lookup"><span data-stu-id="8658c-110">In the following example, `numbers` is the data source and `num` is the range variable.</span></span> <span data-ttu-id="8658c-111">Observe que ambas as variáveis são fortemente tipadas, mesmo com o uso da palavra-chave [var](../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-111">Note that both variables are strongly typed even through the [var](../../../csharp/language-reference/keywords/var.md) keyword is used.</span></span>  
  
 <span data-ttu-id="8658c-112">[!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8658c-112">[!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]</span></span>  
  
## <a name="the-range-variable"></a><span data-ttu-id="8658c-113">A Variável de Intervalo</span><span class="sxs-lookup"><span data-stu-id="8658c-113">The Range Variable</span></span>  
 <span data-ttu-id="8658c-114">O compilador infere que o tipo da variável de intervalo quando a fonte de dados implementa <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8658c-114">The compiler infers the type of the range variable when the data source implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="8658c-115">Por exemplo, se a fonte tem um tipo de `IEnumerable<Customer>`, então, a variável de intervalo será inferida como `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8658c-115">For example, if the source has a type of `IEnumerable<Customer>`, then the range variable is inferred to be `Customer`.</span></span> <span data-ttu-id="8658c-116">O tipo deve ser especificado explicitamente somente quando a fonte for um tipo `IEnumerable` não genérico, como <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="8658c-116">The only time that you must specify the type explicitly is when the source is a non-generic `IEnumerable` type such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="8658c-117">Para obter mais informações, consulte [Como Consultar um ArrayList com LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e).</span><span class="sxs-lookup"><span data-stu-id="8658c-117">For more information, see [How to: Query an ArrayList with LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e).</span></span>  
  
 <span data-ttu-id="8658c-118">No exemplo anterior, `num` é inferido como do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="8658c-118">In the previous example `num` is inferred to be of type `int`.</span></span> <span data-ttu-id="8658c-119">Como a variável de intervalo é fortemente tipada, é possível chamar métodos nela ou usá-la em outras operações.</span><span class="sxs-lookup"><span data-stu-id="8658c-119">Because the range variable is strongly typed, you can call methods on it or use it in other operations.</span></span> <span data-ttu-id="8658c-120">Por exemplo, em vez de gravar `select num`, grave `select num.ToString()` para fazer com que a expressão de consulta retorne uma sequência de cadeias de caracteres em vez de números inteiros.</span><span class="sxs-lookup"><span data-stu-id="8658c-120">For example, instead of writing `select num`, you could write `select num.ToString()` to cause the query expression to return a sequence of strings instead of integers.</span></span> <span data-ttu-id="8658c-121">Também é possível gravar `select n + 10` para fazer com que a expressão retorne a sequência 14, 11, 13, 12, 10.</span><span class="sxs-lookup"><span data-stu-id="8658c-121">Or you could write `select n + 10` to cause the expression to return the sequence 14, 11, 13, 12, 10.</span></span> <span data-ttu-id="8658c-122">Para obter mais informações, consulte [cláusula select](../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-122">For more information, see [select clause](../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
 <span data-ttu-id="8658c-123">A variável de intervalo é como uma variável de iteração em uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md), com a exceção de uma diferença muito importante: na verdade, uma variável de intervalo nunca armazena dados da fonte.</span><span class="sxs-lookup"><span data-stu-id="8658c-123">The range variable is like an iteration variable in a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement except for one very important difference: a range variable never actually stores data from the source.</span></span> <span data-ttu-id="8658c-124">É apenas uma conveniência sintática que habilita a consulta a descrever o que ocorrerá quando ela for executada.</span><span class="sxs-lookup"><span data-stu-id="8658c-124">It just a syntactic convenience that enables the query to describe what will occur when the query is executed.</span></span> <span data-ttu-id="8658c-125">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-125">For more information, see [Introduction to LINQ Queries (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="compound-from-clauses"></a><span data-ttu-id="8658c-126">Cláusulas from compostas</span><span class="sxs-lookup"><span data-stu-id="8658c-126">Compound from Clauses</span></span>  
 <span data-ttu-id="8658c-127">Em alguns casos, cada elemento na sequência de origem pode ser uma sequência ou conter uma sequência.</span><span class="sxs-lookup"><span data-stu-id="8658c-127">In some cases, each element in the source sequence may itself be either a sequence or contain a sequence.</span></span> <span data-ttu-id="8658c-128">Por exemplo, a fonte de dados pode ser um `IEnumerable<Student>` em que cada objeto do aluno na sequência contenha uma lista de resultados de avaliações.</span><span class="sxs-lookup"><span data-stu-id="8658c-128">For example, your data source may be an `IEnumerable<Student>` where each student object in the sequence contains a list of test scores.</span></span> <span data-ttu-id="8658c-129">Para acessar a lista interna dentro de cada elemento `Student`, use cláusulas compostas `from`.</span><span class="sxs-lookup"><span data-stu-id="8658c-129">To access the inner list within each `Student` element, you can use compound `from` clauses.</span></span> <span data-ttu-id="8658c-130">A técnica é parecida com o uso de instruções [foreach](../../../csharp/language-reference/keywords/foreach-in.md) aninhadas.</span><span class="sxs-lookup"><span data-stu-id="8658c-130">The technique is like using nested [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statements.</span></span> <span data-ttu-id="8658c-131">É possível adicionar cláusulas [where](../../../csharp/language-reference/keywords/partial-method.md) ou [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) a qualquer cláusula `from` para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="8658c-131">You can add [where](../../../csharp/language-reference/keywords/partial-method.md) or [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clauses to either `from` clause to filter the results.</span></span> <span data-ttu-id="8658c-132">O exemplo a seguir mostra uma sequência de objetos `Student`, em cada um contém uma `List` interna de inteiros que representam de resultados de avaliações.</span><span class="sxs-lookup"><span data-stu-id="8658c-132">The following example shows a sequence of `Student` objects, each of which contains an inner `List` of integers representing test scores.</span></span> <span data-ttu-id="8658c-133">Para acessar a lista interna, use uma cláusula composta `from`.</span><span class="sxs-lookup"><span data-stu-id="8658c-133">To access the inner list, use a compound `from` clause.</span></span> <span data-ttu-id="8658c-134">É possível inserir cláusulas entre as duas cláusulas `from`, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8658c-134">You can insert clauses between the two `from` clauses if necessary.</span></span>  
  
 <span data-ttu-id="8658c-135">[!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8658c-135">[!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]</span></span>  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a><span data-ttu-id="8658c-136">Usando Várias Cláusulas from para Realizar Uniões</span><span class="sxs-lookup"><span data-stu-id="8658c-136">Using Multiple from Clauses to Perform Joins</span></span>  
 <span data-ttu-id="8658c-137">Uma cláusula composta `from` é usada para acessar coleções internas em uma fonte de dados única.</span><span class="sxs-lookup"><span data-stu-id="8658c-137">A compound `from` clause is used to access inner collections in a single data source.</span></span> <span data-ttu-id="8658c-138">No entanto, uma consulta também pode conter várias cláusulas `from` que geram consultas complementares de fontes de dados independentes.</span><span class="sxs-lookup"><span data-stu-id="8658c-138">However, a query can also contain multiple `from` clauses that generate supplemental queries from independent data sources.</span></span> <span data-ttu-id="8658c-139">Essa técnica habilita a execução de determinados tipos de operações de união que não são possíveis por meio da [cláusula join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-139">This technique enables you to perform certain types of join operations that are not possible by using the [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
 <span data-ttu-id="8658c-140">A exemplo a seguir mostra como duas cláusulas `from` podem ser usadas para formar uma união cruzada completa de duas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="8658c-140">The following example shows how two `from` clauses can be used to form a complete cross join of two data sources.</span></span>  
  
 <span data-ttu-id="8658c-141">[!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8658c-141">[!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]</span></span>  
  
 <span data-ttu-id="8658c-142">Para obter mais informações sobre as operações de união que usam várias cláusulas `from`, consulte [Como Executar Operações de União Personalizadas](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8658c-142">For more information about join operations that use multiple `from` clauses, see [How to: Perform Custom Join Operations](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8658c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8658c-143">See Also</span></span>  
 <span data-ttu-id="8658c-144">[Palavras-chave de Consulta (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="8658c-144">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 [<span data-ttu-id="8658c-145">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="8658c-145">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

