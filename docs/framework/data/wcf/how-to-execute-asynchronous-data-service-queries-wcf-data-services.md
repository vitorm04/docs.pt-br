---
title: Como executar consultas de serviço de dados assíncronos (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 84eb88695580598d41615653723c137d3f766a47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150603"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Como executar consultas de serviço de dados assíncronos (WCF Data Services)

Usando a biblioteca de cliente do WCF Data Services, você pode executar operações de cliente-servidor de forma assíncrona, como executar consultas e salvar alterações. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> Em um aplicativo em que o retorno de chamada deve ser invocado em um thread específico, você deve realizar marshaling explicitamente da execução do <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> método. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir mostra como executar uma consulta assíncrona chamando o <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> método para iniciar a consulta. O delegado embutido chama o <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> método para exibir os resultados da consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Confira também

- [Biblioteca de cliente do WCF Data Services](wcf-data-services-client-library.md)
