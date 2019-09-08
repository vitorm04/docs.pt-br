---
title: 'Como: Habilitar a paginação de resultados do serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780045"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Como: Habilitar a paginação de resultados do serviço de dados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite limitar o número de entidades retornadas por uma consulta de serviço de dados. Os limites de página são definidos no método que é chamado quando o serviço é inicializado e pode ser definido separadamente para cada conjunto de entidades.  
  
 Quando a paginação está habilitada, a entrada final no feed contém um link para a próxima página de dados. Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md).  
  
 Este tópico mostra como modificar um serviço de dados para habilitar a paginação `Orders` de conjuntos de entidades e retornados `Customers` . O exemplo neste tópico usa o serviço de dados de exemplo Northwind. Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Como habilitar a paginação de conjuntos de entidades de clientes e pedidos retornados  
  
- No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Consulte também

- [Carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md)
- [Como: Carregar resultados paginados](how-to-load-paged-results-wcf-data-services.md)
