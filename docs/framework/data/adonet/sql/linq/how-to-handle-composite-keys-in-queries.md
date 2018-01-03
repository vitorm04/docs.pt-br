---
title: 'Como: Manipular teclas compostas em consultas'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b0954d4659d1cc39cead0658fbd21dcd6dd12e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="f3da8-102">Como: Manipular teclas compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="f3da8-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="f3da8-103">Alguns operadores podem levar apenas um argumento.</span><span class="sxs-lookup"><span data-stu-id="f3da8-103">Some operators can take only one argument.</span></span> <span data-ttu-id="f3da8-104">Se o argumento deve incluir mais de uma coluna de base de dados, você deve criar um tipo anônimo para representar a combinação.</span><span class="sxs-lookup"><span data-stu-id="f3da8-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3da8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3da8-105">Example</span></span>  
 <span data-ttu-id="f3da8-106">O exemplo a seguir mostra uma consulta que invoca o operador de `GroupBy` , que pode levar apenas um argumento de `key` .</span><span class="sxs-lookup"><span data-stu-id="f3da8-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="f3da8-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3da8-107">Example</span></span>  
 <span data-ttu-id="f3da8-108">Refere-se a mesma situação join, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f3da8-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f3da8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3da8-109">See Also</span></span>  
 [<span data-ttu-id="f3da8-110">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="f3da8-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
