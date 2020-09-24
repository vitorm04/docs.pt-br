---
title: 'Como: recuperar informações como somente leitura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 0a6853ef5d0b67e5efb95731adb5a106e8701e0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155829"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="1d41c-102">Como: recuperar informações como somente leitura</span><span class="sxs-lookup"><span data-stu-id="1d41c-102">How to: Retrieve Information As Read-Only</span></span>

<span data-ttu-id="1d41c-103">Quando você não pretende modificar os dados, você pode aumentar o desempenho de consultas buscando resultados somente leitura.</span><span class="sxs-lookup"><span data-stu-id="1d41c-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="1d41c-104">Você implementar o processamento somente leitura <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> definindo a `false`.</span><span class="sxs-lookup"><span data-stu-id="1d41c-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d41c-105">Quando <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> é definido como `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> é definido implicitamente a `false`.</span><span class="sxs-lookup"><span data-stu-id="1d41c-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d41c-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d41c-106">Example</span></span>  

 <span data-ttu-id="1d41c-107">O código a seguir recupera uma coleção somente leitura de datas de admissão de funcionários.</span><span class="sxs-lookup"><span data-stu-id="1d41c-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1d41c-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d41c-108">See also</span></span>

- [<span data-ttu-id="1d41c-109">Consulte conceitos</span><span class="sxs-lookup"><span data-stu-id="1d41c-109">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="1d41c-110">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="1d41c-110">Querying the Database</span></span>](querying-the-database.md)
- [<span data-ttu-id="1d41c-111">Adiado contra a carga immediate</span><span class="sxs-lookup"><span data-stu-id="1d41c-111">Deferred versus Immediate Loading</span></span>](deferred-versus-immediate-loading.md)
