---
title: 'Como: manipular chaves compostas em consultas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: bc16dde89f67572b03102b1c091993ed163b443c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203521"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="747fb-102">Como: manipular chaves compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="747fb-102">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="747fb-103">Alguns operadores podem levar apenas um argumento.</span><span class="sxs-lookup"><span data-stu-id="747fb-103">Some operators can take only one argument.</span></span> <span data-ttu-id="747fb-104">Se o argumento deve incluir mais de uma coluna de base de dados, você deve criar um tipo anônimo para representar a combinação.</span><span class="sxs-lookup"><span data-stu-id="747fb-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="747fb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="747fb-105">Example</span></span>  

 <span data-ttu-id="747fb-106">O exemplo a seguir mostra uma consulta que invoca o operador de `GroupBy` , que pode levar apenas um argumento de `key` .</span><span class="sxs-lookup"><span data-stu-id="747fb-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="747fb-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="747fb-107">Example</span></span>  

 <span data-ttu-id="747fb-108">Refere-se a mesma situação join, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="747fb-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="747fb-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="747fb-109">See also</span></span>

- [<span data-ttu-id="747fb-110">Consulte conceitos</span><span class="sxs-lookup"><span data-stu-id="747fb-110">Query Concepts</span></span>](query-concepts.md)
