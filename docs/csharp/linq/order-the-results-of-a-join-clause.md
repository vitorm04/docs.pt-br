---
title: "Ordenar os resultados de uma cláusula join"
description: "Como ordenar os resultados de uma cláusula join."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6272181647bb200c18231c5fc836e3dd1a2d6d55
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="ec201-104">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="ec201-104">Order the results of a join clause</span></span>
<span data-ttu-id="ec201-105">Este exemplo mostra como ordenar os resultados de uma operação de junção.</span><span class="sxs-lookup"><span data-stu-id="ec201-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="ec201-106">Observe que a ordenação é executada após a junção.</span><span class="sxs-lookup"><span data-stu-id="ec201-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="ec201-107">Embora você possa usar uma cláusula `orderby` com uma ou mais sequências de origem antes da junção, normalmente não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="ec201-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="ec201-108">Alguns provedores LINQ não podem preservar essa ordem após a junção.</span><span class="sxs-lookup"><span data-stu-id="ec201-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec201-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec201-109">Example</span></span>  
 <span data-ttu-id="ec201-110">Esta consulta cria uma junção de grupos e classifica os grupos com base no elemento de categoria, que ainda está no escopo.</span><span class="sxs-lookup"><span data-stu-id="ec201-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="ec201-111">Dentro do inicializador de tipo anônimo, uma subconsulta ordena todos os elementos de correspondência da sequência de produtos.</span><span class="sxs-lookup"><span data-stu-id="ec201-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 <span data-ttu-id="ec201-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ec201-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="ec201-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec201-113">See also</span></span>  
 <span data-ttu-id="ec201-114">[Expressões de consulta LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="ec201-114">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="ec201-115">[Cláusula orderby](../language-reference/keywords/orderby-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ec201-115">[orderby clause](../language-reference/keywords/orderby-clause.md) </span></span>  
 [<span data-ttu-id="ec201-116">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="ec201-116">join clause</span></span>](../language-reference/keywords/join-clause.md) 

