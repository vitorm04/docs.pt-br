---
title: 'Como: carregar entidades relacionadas (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: f7aa13ac217d86be23d0957ddb6c069831cacd2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Como: carregar entidades relacionadas (WCF Data Services)
Quando você precisar carregar entidades associadas em [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode usar o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método o <xref:System.Data.Services.Client.DataServiceContext> classe. Você também pode usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método sobre o <xref:System.Data.Services.Client.DataServiceQuery%601> para exigir que as entidades relacionadas ansiosamente sejam carregados na mesma resposta de consulta.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como carregar explicitamente o `Customer` que está relacionado a cada retornado `Orders` instância.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método para retornar `Order Details` que pertencem ao `Orders` retornado pela consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Consulte também  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
