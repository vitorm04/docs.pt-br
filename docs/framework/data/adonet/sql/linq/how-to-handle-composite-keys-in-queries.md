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
ms.openlocfilehash: 168e721eee7f5253412438a2185934f01bf081c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="89525-102">Como: Manipular teclas compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="89525-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="89525-103">Alguns operadores podem levar apenas um argumento.</span><span class="sxs-lookup"><span data-stu-id="89525-103">Some operators can take only one argument.</span></span> <span data-ttu-id="89525-104">Se o argumento deve incluir mais de uma coluna de base de dados, você deve criar um tipo anônimo para representar a combinação.</span><span class="sxs-lookup"><span data-stu-id="89525-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89525-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89525-105">Example</span></span>  
 <span data-ttu-id="89525-106">O exemplo a seguir mostra uma consulta que invoca o operador de `GroupBy` , que pode levar apenas um argumento de `key` .</span><span class="sxs-lookup"><span data-stu-id="89525-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="89525-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89525-107">Example</span></span>  
 <span data-ttu-id="89525-108">Refere-se a mesma situação join, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="89525-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="89525-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89525-109">See Also</span></span>  
 [<span data-ttu-id="89525-110">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="89525-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
