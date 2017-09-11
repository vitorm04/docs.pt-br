---
title: "Operações de consulta LINQ básica (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e5dbebb7950678a0f40ec774d23b42dfe89cff49
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="86318-102">Operações de consulta LINQ básica (C#)</span><span class="sxs-lookup"><span data-stu-id="86318-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="86318-103">Este tópico fornece uma breve introdução às expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e a alguns dos tipos típicos de operações que podem ser executadas em uma consulta.</span><span class="sxs-lookup"><span data-stu-id="86318-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="86318-104">Informações mais detalhadas estão nos tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="86318-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="86318-105">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="86318-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="86318-106">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="86318-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="86318-107">Passo a passo: escrevendo consultas em C#</span><span class="sxs-lookup"><span data-stu-id="86318-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="86318-108">Se já estiver familiarizado com uma linguagem de consulta como SQL ou XQuery, você poderá ignorar a maior parte deste tópico.</span><span class="sxs-lookup"><span data-stu-id="86318-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="86318-109">Leia sobre a "cláusula `from`" na próxima seção para saber mais sobre a ordem das cláusulas em expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="86318-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="86318-110">Obtendo uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="86318-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="86318-111">Em um consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a primeira etapa é especificar a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="86318-111">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="86318-112">No C#, como na maioria das linguagens de programação, uma variável deve ser declarada antes que possa ser usada.</span><span class="sxs-lookup"><span data-stu-id="86318-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="86318-113">Em um consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a cláusula `from` vem primeiro para introduzir a fonte de dados (`customers`) e a *variável de intervalo* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="86318-113">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 <span data-ttu-id="86318-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-114">[!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]</span></span>  
  
 <span data-ttu-id="86318-115">A variável de intervalo é como a variável de iteração em um loop `foreach`, mas nenhuma iteração real ocorre em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="86318-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="86318-116">Quando a consulta é executada, a variável de intervalo servirá como uma referência para cada elemento sucessivo em `customers`.</span><span class="sxs-lookup"><span data-stu-id="86318-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="86318-117">Uma vez que o compilador pode inferir o tipo de `cust`, você não precisa especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="86318-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="86318-118">Variáveis de intervalo adicionais podem ser introduzidas por uma cláusula `let`.</span><span class="sxs-lookup"><span data-stu-id="86318-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="86318-119">Para obter mais informações, consulte [Cláusula let](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-119">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86318-120">Para fontes de dados não genéricas, como <xref:System.Collections.ArrayList>, a variável de intervalo deve ser tipada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="86318-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="86318-121">Para obter mais informações, consulte [Como consultar um ArrayList com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) e [Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-121">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="86318-122">Filtragem</span><span class="sxs-lookup"><span data-stu-id="86318-122">Filtering</span></span>  
 <span data-ttu-id="86318-123">Provavelmente, a operação de consulta mais comum é aplicar um filtro no formulário de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="86318-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="86318-124">O filtro faz com que a consulta retorne apenas os elementos para os quais a expressão é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="86318-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="86318-125">O resultado é produzido usando a cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="86318-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="86318-126">O filtro em vigor especifica os elementos a serem excluídos da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="86318-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="86318-127">No exemplo a seguir, somente os `customers` que têm um endereço em Londres são retornados.</span><span class="sxs-lookup"><span data-stu-id="86318-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 <span data-ttu-id="86318-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-128">[!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]</span></span>  
  
 <span data-ttu-id="86318-129">Você pode usar os operadores lógicos `AND` e `OR` de C# para aplicar quantas expressões de filtro forem necessárias na cláusula `where`.</span><span class="sxs-lookup"><span data-stu-id="86318-129">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="86318-130">Por exemplo, para retornar somente clientes de "Londres" `AND` cujo nome seja "Devon", você escreveria o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="86318-130">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 <span data-ttu-id="86318-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-131">[!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]</span></span>  
  
 <span data-ttu-id="86318-132">Para retornar clientes de Londres ou Paris, você escreveria o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="86318-132">To return customers from London or Paris, you would write the following code:</span></span>  
  
 <span data-ttu-id="86318-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-133">[!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]</span></span>  
  
 <span data-ttu-id="86318-134">Para obter mais informações, consulte [Cláusula where](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-134">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="86318-135">Ordenando</span><span class="sxs-lookup"><span data-stu-id="86318-135">Ordering</span></span>  
 <span data-ttu-id="86318-136">Muitas vezes é conveniente classificar os dados retornados.</span><span class="sxs-lookup"><span data-stu-id="86318-136">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="86318-137">A cláusula `orderby` fará com que os elementos na sequência retornada sejam classificados de acordo com o comparador padrão para o tipo que está sendo classificado.</span><span class="sxs-lookup"><span data-stu-id="86318-137">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="86318-138">Por exemplo, a consulta a seguir pode ser estendida para classificar os resultados com base na propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="86318-138">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="86318-139">Como `Name` é uma cadeia de caracteres, o comparador padrão executa uma classificação em ordem alfabética de A a Z.</span><span class="sxs-lookup"><span data-stu-id="86318-139">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 <span data-ttu-id="86318-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-140">[!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]</span></span>  
  
 <span data-ttu-id="86318-141">Para ordenar os resultados na ordem inversa, de Z para a, use a cláusula `orderby…descending`.</span><span class="sxs-lookup"><span data-stu-id="86318-141">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="86318-142">Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-142">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="86318-143">Agrupamento</span><span class="sxs-lookup"><span data-stu-id="86318-143">Grouping</span></span>  
 <span data-ttu-id="86318-144">A cláusula `group` permite agrupar seus resultados com base em uma chave que você especificar.</span><span class="sxs-lookup"><span data-stu-id="86318-144">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="86318-145">Por exemplo, você pode especificar que os resultados sejam agrupados segundo o `City`, de modo que todos os clientes de Londres ou Paris fiquem em grupos individuais.</span><span class="sxs-lookup"><span data-stu-id="86318-145">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="86318-146">Nesse caso, `cust.City` é a chave.</span><span class="sxs-lookup"><span data-stu-id="86318-146">In this case, `cust.City` is the key.</span></span>  
  
 <span data-ttu-id="86318-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-147">[!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]</span></span>  
  
 <span data-ttu-id="86318-148">Quando você terminar uma consulta com um cláusula `group`, seus resultados assumirão a forma de uma lista de listas.</span><span class="sxs-lookup"><span data-stu-id="86318-148">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="86318-149">Cada elemento na lista é um objeto que tem um membro `Key` e uma lista dos elementos que estão agrupados sob essa chave.</span><span class="sxs-lookup"><span data-stu-id="86318-149">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="86318-150">Quando itera em uma consulta que produz uma sequência de grupos, você deve usar um loop `foreach` aninhado.</span><span class="sxs-lookup"><span data-stu-id="86318-150">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="86318-151">O loop externo itera em cada grupo e o loop interno itera nos membros de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="86318-151">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="86318-152">Se precisar consultar os resultados de uma operação de grupo, você poderá usar a palavra-chave `into` para criar um identificador que pode ser consultado ainda mais.</span><span class="sxs-lookup"><span data-stu-id="86318-152">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="86318-153">A consulta a seguir retorna apenas os grupos que contêm mais de dois clientes:</span><span class="sxs-lookup"><span data-stu-id="86318-153">The following query returns only those groups that contain more than two customers:</span></span>  
  
 <span data-ttu-id="86318-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-154">[!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]</span></span>  
  
 <span data-ttu-id="86318-155">Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-155">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="86318-156">Ingressando</span><span class="sxs-lookup"><span data-stu-id="86318-156">Joining</span></span>  
 <span data-ttu-id="86318-157">Operações de junção criam associações entre sequências que não são modeladas explicitamente nas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="86318-157">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="86318-158">Por exemplo, você pode executar uma junção para localizar todos os clientes e distribuidores que têm o mesmo local.</span><span class="sxs-lookup"><span data-stu-id="86318-158">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="86318-159">Em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a cláusula `join` sempre funciona com coleções de objetos em vez de tabelas de banco de dados diretamente.</span><span class="sxs-lookup"><span data-stu-id="86318-159">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 <span data-ttu-id="86318-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="86318-160">[!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]</span></span>  
  
 <span data-ttu-id="86318-161">Em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], você não precisa usar `join` com a mesma frequência que o faz no SQL, porque as chaves estrangeiras em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] são representados no modelo do objeto como propriedades que mantêm uma coleção de itens.</span><span class="sxs-lookup"><span data-stu-id="86318-161">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="86318-162">Por exemplo, um objeto `Customer` que contém uma coleção de objetos `Order`.</span><span class="sxs-lookup"><span data-stu-id="86318-162">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="86318-163">Em vez de executar uma junção, você pode acessar os pedidos usando notação de ponto:</span><span class="sxs-lookup"><span data-stu-id="86318-163">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="86318-164">Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-164">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="86318-165">Selecionando (Projeções)</span><span class="sxs-lookup"><span data-stu-id="86318-165">Selecting (Projections)</span></span>  
 <span data-ttu-id="86318-166">A cláusula `select` produz os resultados da consulta e especifica a "forma" ou o tipo de cada elemento retornado.</span><span class="sxs-lookup"><span data-stu-id="86318-166">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="86318-167">Por exemplo, você pode especificar se os resultados consistirão em objetos `Customer` completos, apenas um membro, um subconjunto de membros ou algum tipo de resultado completamente diferente com base em um cálculo ou na criação de um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="86318-167">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="86318-168">Quando a cláusula `select` produz algo diferente de uma cópia do elemento de origem, a operação é chamada de *projeção*.</span><span class="sxs-lookup"><span data-stu-id="86318-168">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="86318-169">O uso de projeções para transformar dados é uma funcionalidade poderosa das expressões de consulta de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="86318-169">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="86318-170">Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) e [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="86318-170">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86318-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86318-171">See Also</span></span>  
 <span data-ttu-id="86318-172">[Introdução ao LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="86318-172">[Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 <span data-ttu-id="86318-173">[Expressões de Consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="86318-173">[LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="86318-174">[Passo a passo: escrevendo consultas em C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="86318-174">[Walkthrough: Writing Queries in C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 <span data-ttu-id="86318-175">[Palavras-chave de Consulta (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="86318-175">[Query Keywords (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 [<span data-ttu-id="86318-176">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="86318-176">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

