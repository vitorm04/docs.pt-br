---
title: "Operações de envio em lote (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65bf6bfd0bd437848137506605a958f5f2e8d750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="batching-operations-wcf-data-services"></a>Operações de envio em lote (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dá suporte a lotes de processamento de solicitações para um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviço. Para obter mais informações, consulte [OData: processamento em lote](http://go.microsoft.com/fwlink/?LinkId=186075). Em [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], cada operação que utiliza o <xref:System.Data.Services.Client.DataServiceContext>, como a execução de uma consulta ou salvar as alterações, resulta em uma solicitação separada que estão sendo enviados para o serviço de dados. Para manter um escopo lógico para conjuntos de operações, você pode definir explicitamente os lotes operacionais. Isso garante que todas as operações no lote são enviados para o serviço de dados em uma única solicitação HTTP, permite que o servidor processar as operações atomicamente e reduz o número de idas e voltas para o serviço de dados.  
  
## <a name="batching-query-operations"></a>Operações de consulta de processamento em lotes  
 Para executar várias consultas em um único lote, você deve criar cada consulta no lote como uma instância separada do <xref:System.Data.Services.Client.DataServiceRequest%601> classe. Quando você cria uma solicitação de consulta dessa maneira, a consulta em si é definida como um URI, e ele segue as regras de endereçamento de recursos. Para obter mais informações, consulte [acessando recursos do serviço de dados](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). A consulta em lotes solicitações são enviadas para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> método é chamado que contém os objetos de solicitação de consulta. Este método retorna um <xref:System.Data.Services.Client.DataServiceResponse> objeto, que é uma coleção de <xref:System.Data.Services.Client.QueryOperationResponse%601> objetos que representam as respostas a consultas individuais no lote, cada uma delas contém em uma coleção de objetos retornados pelas informações de erro ou de consulta. Quando qualquer operação única consulta no lote falhar, as informações de erro são retornadas no <xref:System.Data.Services.Client.QueryOperationResponse%601> objeto para a operação que falhou e as operações restantes ainda são executadas. Para obter mais informações, consulte [como: executar consultas em um lote](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Consultas em lote também podem ser executadas de forma assíncrona. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Envio em lote operação SaveChanges  
 Quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método, todas as alterações que o contexto de faixas são convertidas em operações com base em REST que são enviadas como solicitações para o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service. Por padrão, essas alterações não serão enviadas em uma mensagem de solicitação única. Para exigir que todas as alterações de ser enviados em uma única solicitação, você deve chamar o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> método e incluir um valor de <xref:System.Data.Services.Client.SaveChangesOptions.Batch> no <xref:System.Data.Services.Client.SaveChangesOptions> fornecido para o método de enumeração.  
  
 Você pode também assincronamente salvar alterações em lotes. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
