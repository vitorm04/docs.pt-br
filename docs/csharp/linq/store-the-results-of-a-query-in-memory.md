---
title: "Armazenar os resultados de uma consulta na memória"
description: Como armazenar os resultados.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 35d908bde06ef55ba2dc93a73211f7be33b9332c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="70925-104">Armazenar os resultados de uma consulta na memória</span><span class="sxs-lookup"><span data-stu-id="70925-104">Store the results of a query in memory</span></span>

<span data-ttu-id="70925-105">Uma consulta é basicamente um conjunto de instruções sobre como recuperar e organizar os dados.</span><span class="sxs-lookup"><span data-stu-id="70925-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="70925-106">As consultas são executadas lentamente, conforme cada item subsequente no resultado é solicitado.</span><span class="sxs-lookup"><span data-stu-id="70925-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="70925-107">Quando você usa `foreach` para iterar os resultados, os itens são retornados conforme acessado.</span><span class="sxs-lookup"><span data-stu-id="70925-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="70925-108">Para avaliar uma consulta e armazenar os resultados sem executar um loop `foreach`, basta chamar um dos métodos a seguir na variável de consulta:</span><span class="sxs-lookup"><span data-stu-id="70925-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="70925-109">Recomendamos que ao armazenar os resultados da consulta, você atribua o objeto da coleção retornado a uma nova variável conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="70925-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="70925-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70925-110">Example</span></span>  
 <span data-ttu-id="70925-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="70925-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="70925-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70925-112">See Also</span></span>  
 [<span data-ttu-id="70925-113">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="70925-113">LINQ Query Expressions</span></span>](index.md)

