---
title: Como executar consultas em um lote (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: 0ddf5b4f68ca08fca0c55cfcdfcd5431bcec6de2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569047"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>Como executar consultas em um lote (WCF Data Services)
Usando a biblioteca de cliente WCF Data Services, você pode executar mais de uma consulta no serviço de dados em um único lote. Para obter mais informações, consulte [operações de envio em lote](batching-operations-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como chamar o método <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> para executar uma matriz de objetos <xref:System.Data.Services.Client.DataServiceRequest%601> que contém consultas que retornam os objetos `Customers` e `Products` do serviço de dados Northwind. A coleção de objetos <xref:System.Data.Services.Client.QueryOperationResponse%601> no <xref:System.Data.Services.Client.DataServiceResponse> retornado é enumerada e a coleção de objetos contidas em cada <xref:System.Data.Services.Client.QueryOperationResponse%601> também é enumerada.  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
