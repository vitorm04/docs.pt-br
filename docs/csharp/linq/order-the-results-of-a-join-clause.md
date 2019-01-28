---
title: Ordenar os resultados de uma cláusula join (LINQ em C#)
description: Saiba como ordenar os resultados de uma cláusula join de LINQ em C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857882"
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="165fb-103">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="165fb-103">Order the results of a join clause</span></span>

<span data-ttu-id="165fb-104">Este exemplo mostra como ordenar os resultados de uma operação de junção.</span><span class="sxs-lookup"><span data-stu-id="165fb-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="165fb-105">Observe que a ordenação é executada após a junção.</span><span class="sxs-lookup"><span data-stu-id="165fb-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="165fb-106">Embora você possa usar uma cláusula `orderby` com uma ou mais sequências de origem antes da junção, normalmente não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="165fb-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="165fb-107">Alguns provedores LINQ não podem preservar essa ordem após a junção.</span><span class="sxs-lookup"><span data-stu-id="165fb-107">Some LINQ providers might not preserve that ordering after the join.</span></span>

## <a name="example"></a><span data-ttu-id="165fb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="165fb-108">Example</span></span>

<span data-ttu-id="165fb-109">Esta consulta cria uma junção de grupos e classifica os grupos com base no elemento de categoria, que ainda está no escopo.</span><span class="sxs-lookup"><span data-stu-id="165fb-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="165fb-110">Dentro do inicializador de tipo anônimo, uma subconsulta ordena todos os elementos de correspondência da sequência de produtos.</span><span class="sxs-lookup"><span data-stu-id="165fb-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a><span data-ttu-id="165fb-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="165fb-111">See also</span></span>

- [<span data-ttu-id="165fb-112">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="165fb-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="165fb-113">Cláusula orderby</span><span class="sxs-lookup"><span data-stu-id="165fb-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="165fb-114">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="165fb-114">join clause</span></span>](../language-reference/keywords/join-clause.md)
