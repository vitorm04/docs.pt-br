---
title: Como habilitar a paginação de resultados do serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569090"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="50e1c-102">Como habilitar a paginação de resultados do serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="50e1c-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
<span data-ttu-id="50e1c-103">WCF Data Services permite limitar o número de entidades retornadas por uma consulta de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="50e1c-103">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="50e1c-104">Os limites de página são definidos no método que é chamado quando o serviço é inicializado e pode ser definido separadamente para cada conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="50e1c-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="50e1c-105">Quando a paginação está habilitada, a entrada final no feed contém um link para a próxima página de dados.</span><span class="sxs-lookup"><span data-stu-id="50e1c-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="50e1c-106">Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="50e1c-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="50e1c-107">Este tópico mostra como modificar um serviço de dados para habilitar a paginação dos conjuntos de entidades `Customers` e `Orders` retornados.</span><span class="sxs-lookup"><span data-stu-id="50e1c-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="50e1c-108">O exemplo neste tópico usa o serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="50e1c-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="50e1c-109">Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="50e1c-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="50e1c-110">Como habilitar a paginação de conjuntos de entidades de clientes e pedidos retornados</span><span class="sxs-lookup"><span data-stu-id="50e1c-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="50e1c-111">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="50e1c-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="50e1c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50e1c-112">See also</span></span>

- [<span data-ttu-id="50e1c-113">Carregando conteúdo adiado</span><span class="sxs-lookup"><span data-stu-id="50e1c-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="50e1c-114">Como carregar resultados paginados</span><span class="sxs-lookup"><span data-stu-id="50e1c-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
