---
title: 'Como: desligar o carregamento adiado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781660"
---
# <a name="how-to-turn-off-deferred-loading"></a><span data-ttu-id="e639d-102">Como: desligar o carregamento adiado</span><span class="sxs-lookup"><span data-stu-id="e639d-102">How to: Turn Off Deferred Loading</span></span>
<span data-ttu-id="e639d-103">Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="e639d-103">You can turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span> <span data-ttu-id="e639d-104">Para obter mais informações, veja [carregamento deferido versus imediato](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e639d-104">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e639d-105">A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado.</span><span class="sxs-lookup"><span data-stu-id="e639d-105">Deferred loading is turned off by implication when object tracking is turned off.</span></span> <span data-ttu-id="e639d-106">Para obter mais informações, confira [Como: Recuperar informações como somente](how-to-retrieve-information-as-read-only.md)leitura.</span><span class="sxs-lookup"><span data-stu-id="e639d-106">For more information, see [How to: Retrieve Information As Read-Only](how-to-retrieve-information-as-read-only.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e639d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e639d-107">Example</span></span>  
 <span data-ttu-id="e639d-108">O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.</span><span class="sxs-lookup"><span data-stu-id="e639d-108">The following example shows how to turn off deferred loading by setting <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> to `false`.</span></span>  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e639d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e639d-109">See also</span></span>

- [<span data-ttu-id="e639d-110">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="e639d-110">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="e639d-111">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="e639d-111">Querying the Database</span></span>](querying-the-database.md)
