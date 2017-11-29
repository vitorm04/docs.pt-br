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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6bf267cdc4ab3ec3bdc82a3da52cef21ef1d6b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>Como: habilitar a paginação de resultados do serviço de dados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite que você limite o número de entidades retornadas por uma consulta de serviço de dados. Limites de página são definidos no método chamado quando o serviço é inicializado e pode ser definido separadamente para cada conjunto de entidades.  
  
 Quando a paginação estiver habilitada, a entrada final no feed contém um link para a próxima página de dados. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Este tópico mostra como modificar um serviço de dados para habilitar a paginação de retornado `Customers` e `Orders` conjuntos de entidades. O exemplo neste tópico usa o serviço de dados de exemplo Northwind. Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>Como habilitar a paginação retornados Customers e Orders de conjuntos de entidades  
  
-   No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>Consulte também  
 [Carregamento adiado conteúdo](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Como: carregar resultados paginados](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
