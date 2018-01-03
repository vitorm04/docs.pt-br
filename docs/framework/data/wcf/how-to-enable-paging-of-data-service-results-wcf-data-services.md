---
title: "Como: habilitar a paginação de resultados do serviço de dados (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b03dd234681d031361696108702a7bbb558065ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="8cd82-102">Como: habilitar a paginação de resultados do serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8cd82-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="8cd82-103">permite que você limite o número de entidades retornadas por uma consulta de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="8cd82-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="8cd82-104">Limites de página são definidos no método chamado quando o serviço é inicializado e pode ser definido separadamente para cada conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="8cd82-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="8cd82-105">Quando a paginação estiver habilitada, a entrada final no feed contém um link para a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="8cd82-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="8cd82-106">Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8cd82-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="8cd82-107">Este tópico mostra como modificar um serviço de dados para habilitar a paginação de retornado `Customers` e `Orders` conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="8cd82-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="8cd82-108">O exemplo neste tópico usa o serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="8cd82-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="8cd82-109">Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8cd82-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="8cd82-110">Como habilitar a paginação retornados Customers e Orders de conjuntos de entidades</span><span class="sxs-lookup"><span data-stu-id="8cd82-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="8cd82-111">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="8cd82-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="8cd82-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cd82-112">See Also</span></span>  
 [<span data-ttu-id="8cd82-113">Carregando conteúdo adiado</span><span class="sxs-lookup"><span data-stu-id="8cd82-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="8cd82-114">Como carregar resultados paginados</span><span class="sxs-lookup"><span data-stu-id="8cd82-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
