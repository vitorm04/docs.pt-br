---
title: "Visão geral de operadores de consulta padrão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 229b63db761f2a1ed5333fd6f8e4eb9b5c0b75de
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="9765e-102">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="9765e-103">O *operadores de consulta padrão* são os métodos que formam o padrão LINQ.</span><span class="sxs-lookup"><span data-stu-id="9765e-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="9765e-104">A maioria desses métodos operam em sequências, onde uma sequência é um objeto cujo tipo implementa o <xref:System.Collections.Generic.IEnumerable%601>interface ou <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="9765e-105">Operadores de consulta padrão fornecem recursos de consulta, incluindo a filtragem, projeção, agregação, classificação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="9765e-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="9765e-106">Há dois conjuntos de operadores de consulta padrão da LINQ, que opera em objetos de tipo <xref:System.Collections.Generic.IEnumerable%601>e outros que opera em objetos do tipo <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="9765e-107">Os métodos que compõem cada conjunto são membros estáticos de <xref:System.Linq.Enumerable>e <xref:System.Linq.Queryable>classes, respectivamente.</xref:System.Linq.Queryable> </xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="9765e-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="9765e-108">Eles são definidos como *métodos de extensão* do tipo que operam em.</span><span class="sxs-lookup"><span data-stu-id="9765e-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="9765e-109">Isso significa que eles podem ser chamados usando a sintaxe de método estático ou sintaxe de método de instância.</span><span class="sxs-lookup"><span data-stu-id="9765e-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="9765e-110">Além disso, vários métodos de operador de consulta padrão operam em tipos diferentes daqueles com base nos <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="9765e-111">O <xref:System.Linq.Enumerable>tipo define dois métodos que ambos operam em objetos do tipo <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="9765e-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="9765e-112">Esses métodos, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>e <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, permitem que você habilitar uma coleção sem parâmetros ou não genérica, a ser consultado no padrão de LINQ.</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> </xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29></span><span class="sxs-lookup"><span data-stu-id="9765e-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="9765e-113">Eles fazem isso criando uma coleção de objetos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="9765e-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="9765e-114">A <xref:System.Linq.Queryable>classe define dois métodos semelhantes <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>e <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, que operam em objetos do tipo <xref:System.Linq.Queryable>.</xref:System.Linq.Queryable> </xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="9765e-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="9765e-115">Os operadores de consulta padrão são diferentes de tempo de sua execução, dependendo se elas retornam um valor singleton ou uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="9765e-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="9765e-116">Os métodos que retornam um valor singleton (por exemplo, <xref:System.Linq.Enumerable.Average%2A>e <xref:System.Linq.Enumerable.Sum%2A>) são executadas imediatamente.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="9765e-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="9765e-117">Métodos que retornam uma sequência de adiar a execução da consulta e retornam um objeto enumerável.</span><span class="sxs-lookup"><span data-stu-id="9765e-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="9765e-118">No caso de métodos que operam em coleções na memória, ou seja, os métodos que estendem <xref:System.Collections.Generic.IEnumerable%601>, o objeto enumerável retornado captura os argumentos foram passados para o método.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="9765e-119">Quando esse objeto é enumerado, a lógica do operador de consulta é empregada e os resultados da consulta são retornados.</span><span class="sxs-lookup"><span data-stu-id="9765e-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="9765e-120">Por outro lado, métodos que estendem <xref:System.Linq.IQueryable%601>não implementam qualquer comportamento de consulta, mas criar uma árvore de expressão que representa a consulta a ser executada.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="9765e-121">O processamento de consulta é tratado pela origem <xref:System.Linq.IQueryable%601>objeto.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="9765e-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="9765e-122">Chamadas para métodos de consulta podem ser encadeadas em uma consulta, que permite que consultas ser arbitrariamente complexos.</span><span class="sxs-lookup"><span data-stu-id="9765e-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="9765e-123">O exemplo de código a seguir demonstra como os operadores de consulta padrão podem ser usados para obter informações sobre uma sequência.</span><span class="sxs-lookup"><span data-stu-id="9765e-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="9765e-124">Sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="9765e-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="9765e-125">Alguns dos operadores de consulta padrão usados com mais frequência dedicou c# e Visual Basic sintaxe da palavra-chave linguagem que permita a ser chamado como parte de um *consulta* *expressão*.</span><span class="sxs-lookup"><span data-stu-id="9765e-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="9765e-126">Para obter mais informações sobre operadores de consulta padrão que têm palavras-chave e suas sintaxes correspondentes dedicados, consulte [sintaxe de expressão de consulta para operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9765e-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="9765e-127">Estendendo operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="9765e-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="9765e-128">Você pode aumentar o conjunto de operadores de consulta padrão por criando métodos específicos de domínio apropriadas para o domínio de destino ou a tecnologia.</span><span class="sxs-lookup"><span data-stu-id="9765e-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="9765e-129">Você também pode substituir os operadores de consulta padrão com suas próprias implementações que fornecem serviços adicionais, como avaliação remota, a tradução da consulta e a otimização.</span><span class="sxs-lookup"><span data-stu-id="9765e-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="9765e-130">Consulte <xref:System.Linq.Enumerable.AsEnumerable%2A>para obter um exemplo.</xref:System.Linq.Enumerable.AsEnumerable%2A></span><span class="sxs-lookup"><span data-stu-id="9765e-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9765e-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9765e-131">Related Sections</span></span>  
 <span data-ttu-id="9765e-132">Os links a seguir levam você a tópicos que fornecem informações adicionais sobre os vários operadores de consulta padrão com base na funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="9765e-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="9765e-133">Classificando Dados</span><span class="sxs-lookup"><span data-stu-id="9765e-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="9765e-134">Operações de conjunto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="9765e-135">Filtragem de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="9765e-136">Operações de quantificador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="9765e-137">Operações de projeção (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="9765e-138">Particionamento de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="9765e-139">Ingressar em operações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="9765e-140">Agrupando dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="9765e-141">Operações de geração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="9765e-142">Operações de igualdade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="9765e-143">Operações de elemento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="9765e-144">Convertendo tipos de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="9765e-145">Operações de concatenação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="9765e-146">Operações de agregação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9765e-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="9765e-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9765e-147">See Also</span></span>  
 <span data-ttu-id="9765e-148"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="9765e-148"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="9765e-149"><xref:System.Linq.Queryable></xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="9765e-149"><xref:System.Linq.Queryable></span></span>   
<span data-ttu-id="9765e-150"> [Introdução ao LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="9765e-150"> [Introduction to LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="9765e-151"> [Sintaxe de expressão de consulta para operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span><span class="sxs-lookup"><span data-stu-id="9765e-151"> [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span></span>  
<span data-ttu-id="9765e-152"> [Classificação de operadores de consulta padrão por meio da execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span><span class="sxs-lookup"><span data-stu-id="9765e-152"> [Classification of Standard Query Operators by Manner of Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md) </span></span>  
<span data-ttu-id="9765e-153"> [Métodos de Extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="9765e-153"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
