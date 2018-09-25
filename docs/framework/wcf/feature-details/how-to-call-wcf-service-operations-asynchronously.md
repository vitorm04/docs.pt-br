---
title: Como chamar operações de serviço do WCF de maneira assíncrona
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 90e00e4264ff808151c9e1c58fdaf290765620c8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711344"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Como chamar operações de serviço do WCF de maneira assíncrona
Este tópico aborda como um cliente pode acessar uma operação de serviço assincronamente. Implementa o serviço neste tópico o `ICalculator` interface. O cliente pode chamar as operações nesta interface de forma assíncrona usando o modelo de chamada assíncrono controlada por evento. (Para obter mais informações sobre o modelo de chamada assíncrono baseado em evento, consulte [programação Multithreaded com o padrão assíncrono baseado em evento](https://go.microsoft.com/fwlink/?LinkId=248184)). Para obter um exemplo que mostra como implementar uma operação de forma assíncrona em um serviço, consulte [como: implementar uma operação de serviço assíncrona](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Para obter mais informações sobre operações síncronas e assíncronas, consulte [síncrona e operações assíncronas](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  O modelo de chamada assíncrona controlada por evento não é suportado ao usar um <xref:System.ServiceModel.ChannelFactory%601>. Para obter informações sobre como fazer chamadas assíncronas usando o <xref:System.ServiceModel.ChannelFactory%601>, consulte [como: chamar operações de forma assíncrona usando uma fábrica de canais](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Para chamar operações de serviço WCF de forma assíncrona  
  
1.  Execute o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta com ambos os `/async` e o `/tcv:Version35` comando opções juntas, conforme mostrado no comando a seguir.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Isso gera, além de operações síncronas e padrão com base em delegado assíncronas, uma classe de cliente do WCF que contém:  
  
    -   Dois <`operationName` > `Async` operações para uso com a abordagem de chamada assíncrono baseado em evento. Por exemplo:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Eventos da operação foi concluída no formato <`operationName` > `Completed` para uso com a abordagem de chamada assíncrono baseado em evento. Por exemplo:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> tipos de cada operação (no formato <`operationName`>`CompletedEventArgs`) para uso com a abordagem de chamada assíncrono baseado em evento. Por exemplo:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  No aplicativo de chamada, crie um método de retorno de chamada a ser chamado quando a operação assíncrona for concluída, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Antes de chamar a operação, use um novo genérico <xref:System.EventHandler%601?displayProperty=nameWithType> do tipo <`operationName` > `EventArgs` para adicionar o método do manipulador (criado na etapa anterior) para o <`operationName` > `Completed` eventos. Em seguida, chame o <`operationName` > `Async` método. Por exemplo:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Exemplo  
  
> [!NOTE]
>  As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>. Um resultado disso é que, se um cliente importar metadados usando as opções de comando assíncrono baseado em evento e a operação retornar mais de um valor, o padrão <xref:System.EventArgs> objeto retorna um valor como o `Result` são de propriedade e restante Propriedades do <xref:System.EventArgs> objeto. Se você quiser receber o objeto de mensagem como a `Result` propriedade e têm os valores retornados como propriedades nesse objeto, use o `/messageContract` opção de comando. Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>. Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Consulte também  
 [Como implementar uma operação de serviço assíncrona](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
