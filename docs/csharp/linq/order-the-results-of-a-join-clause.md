---
title: "Ordenar os resultados de uma cláusula join"
description: "Como ordenar os resultados de uma cláusula join."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="61d01-104">Ordenar os resultados de uma cláusula join</span><span class="sxs-lookup"><span data-stu-id="61d01-104">Order the results of a join clause</span></span>
<span data-ttu-id="61d01-105">Este exemplo mostra como ordenar os resultados de uma operação de junção.</span><span class="sxs-lookup"><span data-stu-id="61d01-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="61d01-106">Observe que a ordenação é executada após a junção.</span><span class="sxs-lookup"><span data-stu-id="61d01-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="61d01-107">Embora você possa usar uma cláusula `orderby` com uma ou mais sequências de origem antes da junção, normalmente não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="61d01-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="61d01-108">Alguns provedores LINQ não podem preservar essa ordem após a junção.</span><span class="sxs-lookup"><span data-stu-id="61d01-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61d01-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61d01-109">Example</span></span>  
 <span data-ttu-id="61d01-110">Esta consulta cria uma junção de grupos e classifica os grupos com base no elemento de categoria, que ainda está no escopo.</span><span class="sxs-lookup"><span data-stu-id="61d01-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="61d01-111">Dentro do inicializador de tipo anônimo, uma subconsulta ordena todos os elementos de correspondência da sequência de produtos.</span><span class="sxs-lookup"><span data-stu-id="61d01-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="61d01-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61d01-112">See also</span></span>  
 [<span data-ttu-id="61d01-113">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="61d01-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="61d01-114">Cláusula orderby</span><span class="sxs-lookup"><span data-stu-id="61d01-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="61d01-115">Cláusula join</span><span class="sxs-lookup"><span data-stu-id="61d01-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
