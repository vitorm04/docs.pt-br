---
title: 'Como: desligar o carregamento adiado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112951"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="6290b-102">Como: desligar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="6290b-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="6290b-103">Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="6290b-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="6290b-104">Para obter mais informações, consulte [adiada versus imediata Carregando](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="6290b-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6290b-105">A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado.</span><span class="sxs-lookup"><span data-stu-id="6290b-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="6290b-106">Para obter mais informações, confira [Como: Recuperar informações como somente leitura](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="6290b-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6290b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6290b-107">Example</span></span>  
 <span data-ttu-id="6290b-108">O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="6290b-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6290b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6290b-109">See also</span></span>

- [<span data-ttu-id="6290b-110">Consulte conceitos</span><span class="sxs-lookup"><span data-stu-id="6290b-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="6290b-111">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="6290b-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
