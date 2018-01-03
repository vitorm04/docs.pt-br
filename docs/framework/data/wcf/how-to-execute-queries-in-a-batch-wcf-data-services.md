---
title: 'Como: executar consultas em um lote (WCF Data Services)'
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
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01dfb1ac10bdc54f682df4b8af66ba4fd507b705
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Como: executar consultas em um lote (WCF Data Services)
Usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente, você pode executar mais de uma consulta em relação ao serviço de dados em um único lote. Para obter mais informações, consulte [operações em lote](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como chamar o <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> método para executar uma matriz de <xref:System.Data.Services.Client.DataServiceRequest%601> objetos que contém as consultas que retornam ambos `Customers` e `Products` objetos do serviço de dados Northwind. A coleção de <xref:System.Data.Services.Client.QueryOperationResponse%601> objetos retornado <xref:System.Data.Services.Client.DataServiceResponse> é enumerado e a coleção de objetos contidos em cada <xref:System.Data.Services.Client.QueryOperationResponse%601> também é enumerado.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
