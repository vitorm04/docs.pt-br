---
title: 'Como: Filtrar dados relacionados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 9a046c94363a1a161e19dcb68e015f8c6791e511
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703465"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="405b9-102">Como: Filtrar dados relacionados</span><span class="sxs-lookup"><span data-stu-id="405b9-102">How to: Filter Related Data</span></span>
<span data-ttu-id="405b9-103">Use o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> para especificar subpropriedades consultas para limitar a quantidade de dados recuperados.</span><span class="sxs-lookup"><span data-stu-id="405b9-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="405b9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="405b9-104">Example</span></span>  
 <span data-ttu-id="405b9-105">No exemplo a seguir, o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limita `Orders` recuperado com aqueles que não foram enviados hoje.</span><span class="sxs-lookup"><span data-stu-id="405b9-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="405b9-106">Essa abordagem, sem qualquer `Orders` deve ser recuperado mesmo que somente um subconjunto é desejado.</span><span class="sxs-lookup"><span data-stu-id="405b9-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="405b9-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="405b9-107">See also</span></span>
- [<span data-ttu-id="405b9-108">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="405b9-108">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
