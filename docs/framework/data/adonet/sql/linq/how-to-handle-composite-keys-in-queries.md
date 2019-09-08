---
title: 'Como: manipular chaves compostas em consultas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: a6c6e7d1c1d29a049b50f4ea9d70ef5cd9e89a44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793577"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="c5097-102">Como: manipular chaves compostas em consultas</span><span class="sxs-lookup"><span data-stu-id="c5097-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="c5097-103">Alguns operadores podem levar apenas um argumento.</span><span class="sxs-lookup"><span data-stu-id="c5097-103">Some operators can take only one argument.</span></span> <span data-ttu-id="c5097-104">Se o argumento deve incluir mais de uma coluna de base de dados, você deve criar um tipo anônimo para representar a combinação.</span><span class="sxs-lookup"><span data-stu-id="c5097-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5097-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5097-105">Example</span></span>  
 <span data-ttu-id="c5097-106">O exemplo a seguir mostra uma consulta que invoca o operador de `GroupBy` , que pode levar apenas um argumento de `key` .</span><span class="sxs-lookup"><span data-stu-id="c5097-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c5097-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5097-107">Example</span></span>  
 <span data-ttu-id="c5097-108">Refere-se a mesma situação join, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5097-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c5097-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5097-109">See also</span></span>

- [<span data-ttu-id="c5097-110">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="c5097-110">Query Concepts</span></span>](query-concepts.md)
