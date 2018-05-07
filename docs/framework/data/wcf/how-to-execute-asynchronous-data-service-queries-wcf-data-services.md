---
title: 'Como: executar consultas de serviço de dados assíncrono (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 4d8e8f15bbb1efeb0b26e452d1b2a51772be9ed7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Como: executar consultas de serviço de dados assíncrono (WCF Data Services)
Usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente, você pode executar assincronamente operações de cliente-servidor, como executar consultas e salvar as alterações. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  Em um aplicativo em que o retorno de chamada deve ser chamado em um segmento específico, você deve explicitamente empacotar a execução do <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> método. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como executar uma consulta assíncrona chamando o <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> método para iniciar a consulta. Embutido delegar chama o <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> método para exibir os resultados da consulta.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
