---
title: 'Como: desligar o carregamento adiado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938683"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="d7155-102">Como: desligar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="d7155-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="d7155-103">Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="d7155-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="d7155-104">Para obter mais informações, veja [carregamento deferido versus imediato](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="d7155-104">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7155-105">A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado.</span><span class="sxs-lookup"><span data-stu-id="d7155-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="d7155-106">Para obter mais informações, confira [Como: Recuperar informações como somente](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)leitura.</span><span class="sxs-lookup"><span data-stu-id="d7155-106">For more information, see [How to: Retrieve Information As Read-Only](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7155-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7155-107">Example</span></span>  
 <span data-ttu-id="d7155-108">O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="d7155-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d7155-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7155-109">See also</span></span>

- [<span data-ttu-id="d7155-110">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="d7155-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="d7155-111">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="d7155-111">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
