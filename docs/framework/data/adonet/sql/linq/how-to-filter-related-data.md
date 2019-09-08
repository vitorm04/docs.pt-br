---
title: 'Como: filtrar dados relacionados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e8e63c139f38d6de46390925428e18682a65818d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793596"
---
# <a name="how-to-filter-related-data"></a><span data-ttu-id="f6b32-102">Como: filtrar dados relacionados</span><span class="sxs-lookup"><span data-stu-id="f6b32-102">How to: Filter Related Data</span></span>
<span data-ttu-id="f6b32-103">Use o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> para especificar subpropriedades consultas para limitar a quantidade de dados recuperados.</span><span class="sxs-lookup"><span data-stu-id="f6b32-103">Use the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method to specify sub-queries to limit the amount of retrieved data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b32-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6b32-104">Example</span></span>  
 <span data-ttu-id="f6b32-105">No exemplo a seguir, o método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limita `Orders` recuperado com aqueles que não foram enviados hoje.</span><span class="sxs-lookup"><span data-stu-id="f6b32-105">In the following example, the <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method limits the `Orders` retrieved to those that have not been shipped today.</span></span> <span data-ttu-id="f6b32-106">Essa abordagem, sem qualquer `Orders` deve ser recuperado mesmo que somente um subconjunto é desejado.</span><span class="sxs-lookup"><span data-stu-id="f6b32-106">Without this approach, all `Orders` would have been retrieved even though only a subset is desired.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b32-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6b32-107">See also</span></span>

- [<span data-ttu-id="f6b32-108">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="f6b32-108">Querying the Database</span></span>](querying-the-database.md)
