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
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Como habilitar a paginação de resultados do serviço de dados (WCF Data Services)
WCF Data Services permite limitar o número de entidades retornadas por uma consulta de serviço de dados. Os limites de página são definidos no método que é chamado quando o serviço é inicializado e pode ser definido separadamente para cada conjunto de entidades.  
  
 Quando a paginação está habilitada, a entrada final no feed contém um link para a próxima página de dados. Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md).  
  
 Este tópico mostra como modificar um serviço de dados para habilitar a paginação dos conjuntos de entidades `Customers` e `Orders` retornados. O exemplo neste tópico usa o serviço de dados de exemplo Northwind. Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Como habilitar a paginação de conjuntos de entidades de clientes e pedidos retornados  
  
- No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Consulte também

- [Carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md)
- [Como carregar resultados paginados](how-to-load-paged-results-wcf-data-services.md)
