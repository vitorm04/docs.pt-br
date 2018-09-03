---
title: Armazenar os resultados de uma consulta na memória
description: Como armazenar os resultados.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 98a300b2c11eb037ed4ce34caea2673a4e0f8e6b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258076"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="b4512-103">Armazenar os resultados de uma consulta na memória</span><span class="sxs-lookup"><span data-stu-id="b4512-103">Store the results of a query in memory</span></span>

<span data-ttu-id="b4512-104">Uma consulta é basicamente um conjunto de instruções sobre como recuperar e organizar os dados.</span><span class="sxs-lookup"><span data-stu-id="b4512-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="b4512-105">As consultas são executadas lentamente, conforme cada item subsequente no resultado é solicitado.</span><span class="sxs-lookup"><span data-stu-id="b4512-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="b4512-106">Quando você usa `foreach` para iterar os resultados, os itens são retornados conforme acessado.</span><span class="sxs-lookup"><span data-stu-id="b4512-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="b4512-107">Para avaliar uma consulta e armazenar os resultados sem executar um loop `foreach`, basta chamar um dos métodos a seguir na variável de consulta:</span><span class="sxs-lookup"><span data-stu-id="b4512-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="b4512-108">Recomendamos que ao armazenar os resultados da consulta, você atribua o objeto da coleção retornado a uma nova variável conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b4512-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="b4512-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4512-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="b4512-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4512-110">See also</span></span>

- [<span data-ttu-id="b4512-111">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="b4512-111">Language Integrated Query (LINQ)</span></span>](index.md)