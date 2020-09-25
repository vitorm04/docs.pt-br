---
title: 'Como: desligar o carregamento adiado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196956"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="a13ec-102">Como: desligar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="a13ec-102">How to: Turn Off Deferred Loading</span></span>

<span data-ttu-id="a13ec-103">Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="a13ec-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="a13ec-104">Para obter mais informações, veja [carregamento deferido versus imediato](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a13ec-105">A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado.</span><span class="sxs-lookup"><span data-stu-id="a13ec-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="a13ec-106">Para obter mais informações, consulte [como recuperar informações como somente leitura](how-to-retrieve-information-as-read-only.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a13ec-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a13ec-107">Example</span></span>  

 <span data-ttu-id="a13ec-108">O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="a13ec-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a13ec-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="a13ec-109">See also</span></span>

- [<span data-ttu-id="a13ec-110">Consulte conceitos</span><span class="sxs-lookup"><span data-stu-id="a13ec-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="a13ec-111">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="a13ec-111">Querying the Database</span></span>](querying-the-database.md)
