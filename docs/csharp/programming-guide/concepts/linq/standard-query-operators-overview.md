---
title: "Visão geral de operadores de consulta padrão (C#)"
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
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffb68dd9c1a488e1367117bae639805ba9167551
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="832aa-102">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="832aa-103">Os *operadores de consulta padrão* são os métodos que formam o padrão LINQ.</span><span class="sxs-lookup"><span data-stu-id="832aa-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="832aa-104">A maioria desses métodos opera em sequências; neste contexto, uma sequência é um objeto cujo tipo implementa a interface <xref:System.Collections.Generic.IEnumerable%601> ou a interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="832aa-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="832aa-105">Os operadores de consulta padrão fornecem recursos de consulta incluindo filtragem, projeção, agregação, classificação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="832aa-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="832aa-106">Há dois conjuntos de operadores de consulta padrão LINQ, um que opera em objetos do tipo <xref:System.Collections.Generic.IEnumerable%601> e o outro que opera em objetos do tipo <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="832aa-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="832aa-107">Os métodos que compõem a cada conjunto são os membros estáticos das classes <xref:System.Linq.Enumerable> e <xref:System.Linq.Queryable>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="832aa-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="832aa-108">Eles são definidos como *métodos de extensão* do tipo nos quais operam.</span><span class="sxs-lookup"><span data-stu-id="832aa-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="832aa-109">Isso significa que eles podem ser chamados usando a sintaxe de método estático ou sintaxe de método de instância.</span><span class="sxs-lookup"><span data-stu-id="832aa-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="832aa-110">Além disso, vários métodos de operador de consulta padrão operam em tipos diferentes daqueles baseados em <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="832aa-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="832aa-111">O tipo <xref:System.Linq.Enumerable> define dois métodos tais que ambos operam em objetos do tipo <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="832aa-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="832aa-112">Esses métodos, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> e <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, permitem que você habilite uma coleção sem parâmetros ou não genérica, a ser consultada no padrão LINQ.</span><span class="sxs-lookup"><span data-stu-id="832aa-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="832aa-113">Eles fazem isso criando uma coleção de objetos fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="832aa-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="832aa-114">A classe <xref:System.Linq.Queryable> define dois métodos semelhantes, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> e <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, que operam em objetos do tipo <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="832aa-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="832aa-115">Os operadores de consulta padrão são diferentes no momento de sua execução, dependendo de se eles retornam um valor singleton ou uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="832aa-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="832aa-116">Esses métodos que retornam um valor singleton (por exemplo, <xref:System.Linq.Enumerable.Average%2A> e <xref:System.Linq.Enumerable.Sum%2A>) são executados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="832aa-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="832aa-117">Os métodos que retornam uma sequência adiam a execução da consulta e retornam um objeto enumerável.</span><span class="sxs-lookup"><span data-stu-id="832aa-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="832aa-118">No caso de métodos que operam em coleções na memória, ou seja, os métodos que estendem <xref:System.Collections.Generic.IEnumerable%601>, o objeto enumerável retornado captura o argumento que foi passado para o método.</span><span class="sxs-lookup"><span data-stu-id="832aa-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="832aa-119">Quando esse objeto é enumerado, a lógica do operador de consulta é empregada e os resultados da consulta são retornados.</span><span class="sxs-lookup"><span data-stu-id="832aa-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="832aa-120">Por outro lado, os métodos que estendem <xref:System.Linq.IQueryable%601> não implementam nenhum comportamento de consulta, mas criam uma árvore de expressão que representa a consulta a ser executada.</span><span class="sxs-lookup"><span data-stu-id="832aa-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="832aa-121">O processamento de consulta é tratado pelo objeto <xref:System.Linq.IQueryable%601> de origem.</span><span class="sxs-lookup"><span data-stu-id="832aa-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="832aa-122">Chamadas para métodos de consulta podem ser encadeadas em uma consulta, o que permite que consultas se tornem arbitrariamente complexas.</span><span class="sxs-lookup"><span data-stu-id="832aa-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="832aa-123">O exemplo de código a seguir demonstra como os operadores de consulta padrão podem ser usados para obter informações sobre uma sequência.</span><span class="sxs-lookup"><span data-stu-id="832aa-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="832aa-124">Sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="832aa-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="832aa-125">Alguns dos operadores de consulta padrão mais usados têm uma sintaxe de palavra-chave de linguagem C# e Visual Basic dedicada que possibilita que eles sejam chamados como parte de uma *expressão* *de consulta*.</span><span class="sxs-lookup"><span data-stu-id="832aa-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="832aa-126">Para obter mais informações sobre operadores de consulta padrão que têm palavras-chave dedicadas e suas sintaxes correspondentes, consulte [Sintaxe de expressão de consulta para operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="832aa-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="832aa-127">Estendendo os operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="832aa-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="832aa-128">Você pode aumentar o conjunto de operadores de consulta padrão criando métodos específicos de domínio apropriados para o domínio ou tecnologia de destino.</span><span class="sxs-lookup"><span data-stu-id="832aa-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="832aa-129">Você também pode substituir os operadores de consulta padrão por suas próprias implementações que fornecem serviços adicionais, como avaliação remota, conversão de consulta e otimização.</span><span class="sxs-lookup"><span data-stu-id="832aa-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="832aa-130">Para ver um exemplo, consulte <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="832aa-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="832aa-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="832aa-131">Related Sections</span></span>  
 <span data-ttu-id="832aa-132">Os links a seguir levam você a tópicos que fornecem informações adicionais sobre os vários operadores de consulta padrão com base na funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="832aa-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="832aa-133">Classificando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="832aa-134">Operações de conjunto (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="832aa-135">Filtrando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="832aa-136">Operações de quantificador (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="832aa-137">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="832aa-138">Particionando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="832aa-139">Operações de junção (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="832aa-140">Agrupando dados (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="832aa-141">Operações de geração (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="832aa-142">Operações de Igualdade (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="832aa-143">Operações de elemento (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="832aa-144">Convertendo Tipos de Dados (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="832aa-145">Operações de concatenação (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="832aa-146">Operações de agregação (C#)</span><span class="sxs-lookup"><span data-stu-id="832aa-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="832aa-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="832aa-147">See Also</span></span>  
 <span data-ttu-id="832aa-148"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="832aa-148"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="832aa-149"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="832aa-149"><xref:System.Linq.Queryable></span></span>   
 <span data-ttu-id="832aa-150">[Introdução a consultas LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) </span><span class="sxs-lookup"><span data-stu-id="832aa-150">[Introduction to LINQ Queries (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) </span></span>  
 <span data-ttu-id="832aa-151">[Sintaxe de expressão de consulta para operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span><span class="sxs-lookup"><span data-stu-id="832aa-151">[Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span></span>  
 <span data-ttu-id="832aa-152">[Classificação de operadores de consulta padrão pelo modo de execução (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span><span class="sxs-lookup"><span data-stu-id="832aa-152">[Classification of Standard Query Operators by Manner of Execution (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span></span>  
 [<span data-ttu-id="832aa-153">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="832aa-153">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

