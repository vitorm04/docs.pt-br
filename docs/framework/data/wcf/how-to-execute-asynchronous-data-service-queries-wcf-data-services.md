---
title: 'Como: Executar consultas do serviço de dados assíncronos (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 14bfc138c5ece45184fb939f19aaf3d7e73e7294
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790575"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Como: Executar consultas do serviço de dados assíncronos (WCF Data Services)
Usando a biblioteca [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de cliente, você pode executar operações de cliente-servidor de forma assíncrona, como executar consultas e salvar alterações. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> Em um aplicativo em que o retorno de chamada deve ser invocado em um thread específico, você deve realizar marshaling explicitamente da execução do <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> método. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como executar uma consulta assíncrona chamando o <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> método para iniciar a consulta. O delegado embutido chama <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> o método para exibir os resultados da consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
