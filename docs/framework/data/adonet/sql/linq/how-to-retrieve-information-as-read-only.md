---
title: 'Como: recuperar informações como somente leitura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 131562e9ee0fbfde8c94f580bcb6d452918f42ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148974"
---
# <a name="how-to-retrieve-information-as-read-only"></a><span data-ttu-id="ac300-102">Como: recuperar informações como somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac300-102">How to: Retrieve Information As Read-Only</span></span>
<span data-ttu-id="ac300-103">Quando você não pretende modificar os dados, você pode aumentar o desempenho de consultas buscando resultados somente leitura.</span><span class="sxs-lookup"><span data-stu-id="ac300-103">When you do not intend to change the data, you can increase the performance of queries by seeking read-only results.</span></span>  
  
 <span data-ttu-id="ac300-104">Você implementar o processamento somente leitura <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> definindo a `false`.</span><span class="sxs-lookup"><span data-stu-id="ac300-104">You implement read-only processing by setting <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac300-105">Quando <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> é definido como `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> é definido implicitamente a `false`.</span><span class="sxs-lookup"><span data-stu-id="ac300-105">When <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> is set to `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> is implicitly set to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac300-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac300-106">Example</span></span>  
 <span data-ttu-id="ac300-107">O código a seguir recupera uma coleção somente leitura de datas de admissão de funcionários.</span><span class="sxs-lookup"><span data-stu-id="ac300-107">The following code retrieves a read-only collection of employee hire dates.</span></span>  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ac300-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac300-108">See also</span></span>

- [<span data-ttu-id="ac300-109">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="ac300-109">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="ac300-110">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="ac300-110">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
- [<span data-ttu-id="ac300-111">Carregamento adiado versus imediato</span><span class="sxs-lookup"><span data-stu-id="ac300-111">Deferred versus Immediate Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
