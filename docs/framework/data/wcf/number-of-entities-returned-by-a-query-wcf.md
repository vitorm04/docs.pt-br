---
title: "Como: determinar o número de entidades retornadas por uma consulta (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d80e18f780ac164ae83e538c714fc770f4d36e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Como: determinar o número de entidades retornadas por uma consulta (WCF Data Services)
Com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode determinar o número de entidades que estão no conjunto especificada por uma consulta de URI de entidades. Essa contagem pode ser incluída junto com o resultado da consulta ou como um valor inteiro. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo executa uma consulta depois de chamar o <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> método. O <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> propriedade retorna o número de entidades a `Customers` conjunto de entidades.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo chama o <xref:System.Linq.Enumerable.Count%2A> valor de método para retornar apenas um inteiro que é o número de entidades a `Customers` conjunto de entidades.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Consulte também  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
