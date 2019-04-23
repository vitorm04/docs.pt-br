---
title: Operações de envio em lote (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: a9f74f025af6dfc5737ea9f4971f68c5ad913e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133590"
---
# <a name="batching-operations-wcf-data-services"></a>Operações de envio em lote (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dá suporte ao processamento de solicitações do lote uma [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-com base em serviço. Para obter mais informações, consulte [OData: O processamento em lotes](https://go.microsoft.com/fwlink/?LinkId=186075). Na [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], cada operação que utiliza o <xref:System.Data.Services.Client.DataServiceContext>, como executar uma consulta ou salvar as alterações, resulta em uma solicitação separada que estão sendo enviados para o serviço de dados. Para manter um escopo lógico para conjuntos de operações, você pode definir explicitamente os lotes operacionais. Isso garante que todas as operações no lote são enviadas ao serviço de dados em uma única solicitação HTTP, permite que o servidor processar as operações de forma atômica e reduz o número de viagens de ida e volta ao serviço de dados.  
  
## <a name="batching-query-operations"></a>Operações de consulta em lotes  
 Para executar várias consultas em um único lote, você deve criar cada consulta no lote como uma instância separada do <xref:System.Data.Services.Client.DataServiceRequest%601> classe. Quando você cria uma solicitação de consulta dessa maneira, a consulta em si é definida como um URI, e ele segue as regras para endereçar recursos. Para obter mais informações, consulte [acessando recursos do serviço](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md). A consulta em lote as solicitações são enviadas para os dados de serviço quando o <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> método é chamado que contém os objetos de solicitação de consulta. Esse método retorna um <xref:System.Data.Services.Client.DataServiceResponse> objeto, que é uma coleção de <xref:System.Data.Services.Client.QueryOperationResponse%601> objetos que representam as respostas para consultas individuais no lote, cada uma delas contém em uma coleção de objetos retornados pelas informações de erro ou de consulta. Quando qualquer operação única consulta no lote falhar, as informações de erro são retornadas no <xref:System.Data.Services.Client.QueryOperationResponse%601> objeto para a operação que falhou e as operações restantes ainda são executadas. Para obter mais informações, confira [Como: Executar consultas em um lote](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Consultas em lote também podem ser executadas de forma assíncrona. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Envio em lote operação SaveChanges  
 Quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método, todas as alterações que o contexto de faixas são convertidas em operações baseadas em REST que são enviadas como solicitações para o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service. Por padrão, essas alterações não são enviadas em uma mensagem de solicitação única. Para exigir que todas as alterações enviada em uma única solicitação, você deve chamar o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> método e incluir um valor de <xref:System.Data.Services.Client.SaveChangesOptions.Batch> no <xref:System.Data.Services.Client.SaveChangesOptions> enumeração que você fornecer para o método.  
  
 Também de forma assíncrona, você pode salvar as alterações em lote. Para obter mais informações, consulte [operações assíncronas](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
