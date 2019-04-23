---
title: 'Como: Carregar entidades relacionadas (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 75e1d583d2a4d519619a440800cdeb1403fedac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517506"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Como: Carregar entidades relacionadas (WCF Data Services)
Quando você precisa carregar entidades associadas no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode usar o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método o <xref:System.Data.Services.Client.DataServiceContext> classe. Você também pode usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método no <xref:System.Data.Services.Client.DataServiceQuery%601> para exigir que entidades relacionadas avidamente carregados na mesma resposta de consulta.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como carregar explicitamente o `Customer` que está relacionado a cada retornado `Orders` instância.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método para retornar `Order Details` que pertencem ao `Orders` retornados pela consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Consulte também

- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
