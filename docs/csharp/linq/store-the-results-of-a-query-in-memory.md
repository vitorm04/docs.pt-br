---
title: "Armazenar os resultados de uma consulta na memória"
description: Como armazenar os resultados.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="d573c-104">Armazenar os resultados de uma consulta na memória</span><span class="sxs-lookup"><span data-stu-id="d573c-104">Store the results of a query in memory</span></span>

<span data-ttu-id="d573c-105">Uma consulta é basicamente um conjunto de instruções sobre como recuperar e organizar os dados.</span><span class="sxs-lookup"><span data-stu-id="d573c-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="d573c-106">As consultas são executadas lentamente, conforme cada item subsequente no resultado é solicitado.</span><span class="sxs-lookup"><span data-stu-id="d573c-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="d573c-107">Quando você usa `foreach` para iterar os resultados, os itens são retornados conforme acessado.</span><span class="sxs-lookup"><span data-stu-id="d573c-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="d573c-108">Para avaliar uma consulta e armazenar os resultados sem executar um loop `foreach`, basta chamar um dos métodos a seguir na variável de consulta:</span><span class="sxs-lookup"><span data-stu-id="d573c-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="d573c-109">Recomendamos que ao armazenar os resultados da consulta, você atribua o objeto da coleção retornado a uma nova variável conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d573c-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="d573c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d573c-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="d573c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d573c-111">See Also</span></span>  
 [<span data-ttu-id="d573c-112">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="d573c-112">LINQ Query Expressions</span></span>](index.md)
