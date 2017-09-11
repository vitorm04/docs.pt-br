---
title: "Sintaxe de expressão de consulta para operadores de consulta padrão (C#)"
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
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
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
ms.openlocfilehash: 30e994329234b8bd455f739694e50121bac63d5d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a><span data-ttu-id="18990-102">Sintaxe de expressão de consulta para operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="18990-102">Query Expression Syntax for Standard Query Operators (C#)</span></span>
<span data-ttu-id="18990-103">Alguns dos operadores de consulta padrão mais usados têm uma sintaxe de palavra-chave de linguagem C# dedicada que possibilita que eles sejam chamados como parte de uma *expressão de consulta*.</span><span class="sxs-lookup"><span data-stu-id="18990-103">Some of the more frequently used standard query operators have dedicated C# language keyword syntax that enables them to be called as part of a *query expression*.</span></span> <span data-ttu-id="18990-104">Uma expressão de consulta é uma maneira diferente e mais legível de expressar uma consulta do que seu equivalente *baseado em método*.</span><span class="sxs-lookup"><span data-stu-id="18990-104">A query expression is a different, more readable form of expressing a query than its *method-based*  equivalent.</span></span> <span data-ttu-id="18990-105">As cláusulas de expressão de consulta são convertidas em chamadas para os métodos de consulta em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="18990-105">Query expression clauses are translated into calls to the query methods at compile time.</span></span>  
  
## <a name="query-expression-syntax-table"></a><span data-ttu-id="18990-106">Tabela de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="18990-106">Query Expression Syntax Table</span></span>  
 <span data-ttu-id="18990-107">A tabela a seguir lista os operadores de consulta padrão que têm cláusulas de expressão de consulta equivalentes.</span><span class="sxs-lookup"><span data-stu-id="18990-107">The following table lists the standard query operators that have equivalent query expression clauses.</span></span>  
  
|<span data-ttu-id="18990-108">Método</span><span class="sxs-lookup"><span data-stu-id="18990-108">Method</span></span>|<span data-ttu-id="18990-109">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="18990-109">C# Query Expression Syntax</span></span>|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|<span data-ttu-id="18990-110">Use uma variável de intervalo de tipo explícito, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="18990-110">Use an explicitly typed range variable, for example:</span></span><br /><br /> `from int i in numbers`<br /><br /> <span data-ttu-id="18990-111">(Para obter mais informações, consulte [Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-111">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> <span data-ttu-id="18990-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="18990-112">-or-</span></span><br /><br /> `group … by … into …`<br /><br /> <span data-ttu-id="18990-113">(Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-113">(For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> <span data-ttu-id="18990-114">(Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-114">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> <span data-ttu-id="18990-115">(Para obter mais informações, consulte [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-115">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> <span data-ttu-id="18990-116">(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-116">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> <span data-ttu-id="18990-117">(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-117">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> <span data-ttu-id="18990-118">(Para obter mais informações, consulte [Cláusula select](../../../../csharp/language-reference/keywords/select-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-118">(For more information, see [select clause](../../../../csharp/language-reference/keywords/select-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<span data-ttu-id="18990-119">Várias cláusulas `from`.</span><span class="sxs-lookup"><span data-stu-id="18990-119">Multiple `from` clauses.</span></span><br /><br /> <span data-ttu-id="18990-120">(Para obter mais informações, consulte [Cláusula from](../../../../csharp/language-reference/keywords/from-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-120">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> <span data-ttu-id="18990-121">(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-121">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> <span data-ttu-id="18990-122">(Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-122">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> <span data-ttu-id="18990-123">(Para obter mais informações, consulte [Cláusula where](../../../../csharp/language-reference/keywords/where-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="18990-123">(For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18990-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18990-124">See Also</span></span>  
 <span data-ttu-id="18990-125"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="18990-125"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="18990-126"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="18990-126"><xref:System.Linq.Queryable></span></span>   
 <span data-ttu-id="18990-127">[Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="18990-127">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="18990-128">Classificação de operadores de consulta padrão pelo modo de execução (C#)</span><span class="sxs-lookup"><span data-stu-id="18990-128">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)

