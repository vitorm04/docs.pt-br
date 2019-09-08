---
title: Operações de envio em lote (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 2a642bdfd6a8891c54c01a07609760bede2f5d5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780505"
---
# <a name="batching-operations-wcf-data-services"></a>Operações de envio em lote (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] dá suporte ao processamento em lotes de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]solicitações para um serviço baseado em. Para obter mais informações, [consulte OData: Processamento](https://go.microsoft.com/fwlink/?LinkId=186075)em lotes. No [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], cada operação que usa o <xref:System.Data.Services.Client.DataServiceContext>, como executar uma consulta ou salvar alterações, resulta em uma solicitação separada sendo enviada ao serviço de dados. Para manter um escopo lógico para conjuntos de operações, você pode definir explicitamente lotes operacionais. Isso garante que todas as operações no lote sejam enviadas ao serviço de dados em uma única solicitação HTTP, permite que o servidor processe as operações atomicamente e reduz o número de viagens de ida e volta ao serviço de dados.  
  
## <a name="batching-query-operations"></a>Operações de consulta em lote  
 Para executar várias consultas em um único lote, você deve criar cada consulta no lote como uma instância separada da <xref:System.Data.Services.Client.DataServiceRequest%601> classe. Quando você cria uma solicitação de consulta dessa maneira, a própria consulta é definida como um URI e segue as regras para endereçamento de recursos. Para obter mais informações, consulte [acessando recursos do serviço de dados](accessing-data-service-resources-wcf-data-services.md). As solicitações de consulta em lote são enviadas ao serviço de dados quando <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> o método é chamado que contém os objetos de solicitação de consulta. Esse método retorna um <xref:System.Data.Services.Client.DataServiceResponse> objeto, que é uma coleção de <xref:System.Data.Services.Client.QueryOperationResponse%601> objetos que representam respostas a consultas individuais no lote, cada um contendo uma coleção de objetos retornados pela consulta ou informações de erro. Quando uma única operação de consulta no lote falha, as informações de erro são retornadas no <xref:System.Data.Services.Client.QueryOperationResponse%601> objeto para a operação que falhou e as operações restantes ainda são executadas. Para obter mais informações, confira [Como: Execute consultas em um lote](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 As consultas em lote também podem ser executadas de forma assíncrona. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Envio em lote da operação SaveChanges  
 Quando você chama o <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método, todas as alterações que as faixas de contexto são convertidas em operações baseadas em REST que são enviadas [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] como solicitações ao serviço. Por padrão, essas alterações não são enviadas em uma única mensagem de solicitação. Para exigir que todas as alterações sejam enviadas em uma única solicitação, você deve chamar <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> o método e incluir um valor <xref:System.Data.Services.Client.SaveChangesOptions.Batch> de na <xref:System.Data.Services.Client.SaveChangesOptions> enumeração que você fornece ao método.  
  
 Você também pode salvar as alterações em lote de forma assíncrona. Para obter mais informações, consulte [operações assíncronas](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
