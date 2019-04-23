---
title: 'Como: chamar operações assíncronas usando uma fábrica de canais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 17b6dd979f7554cd433cc1abcf2a4da8dd9b83cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772661"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Como: chamar operações assíncronas usando uma fábrica de canais
Este tópico aborda como um cliente pode acessar uma operação de serviço assincronamente ao usar um <xref:System.ServiceModel.ChannelFactory%601>-com base em aplicativo cliente. (Ao usar um <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objeto no qual invocar um serviço que você pode usar o modelo de chamada assíncrona controlada por evento. Para obter mais informações, confira [Como: Chamar operações de serviço de forma assíncrona](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Para obter mais informações sobre o modelo de chamada assíncrono baseado em evento, consulte [padrão assíncrono baseado em evento (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Implementa o serviço neste tópico o `ICalculator` interface. O cliente pode chamar as operações nesta interface de forma assíncrona, o que significa que operações com `Add` são divididas em dois métodos, `BeginAdd` e `EndAdd`, a primeira opção que inicia a chamada e recupera o último resultado Quando a operação for concluída. Para obter um exemplo que mostra como implementar uma operação de forma assíncrona em um serviço, consulte [como: Implementar uma operação de serviço assíncrona](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Para obter detalhes sobre as operações síncronas e assíncronas, consulte [síncrona e operações assíncronas](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Para chamar operações de serviço WCF de forma assíncrona  
  
1. Execute o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta com o `/async` opção conforme mostrado no comando a seguir.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Isso gera uma versão de cliente assíncrono do contrato de serviço para a operação.  
  
2. Crie uma função de retorno de chamada a ser chamado quando a operação assíncrona for concluída, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Para acessar uma operação de serviço de forma assíncrona, criar o cliente e a chamada a `Begin[Operation]` (por exemplo, `BeginAdd`) e especificar uma função de retorno de chamada, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Quando a função de retorno de chamada é executado, o cliente chama `End<operation>` (por exemplo, `EndAdd`) para recuperar o resultado.  
  
## <a name="example"></a>Exemplo  
 O serviço que é usado com o código do cliente que é usado no procedimento anterior implementa o `ICalculator` interface conforme mostrado no código a seguir. No lado do serviço, o `Add` e `Subtract` operações do contrato são invocadas sincronicamente, o Windows Communication Foundation (WCF) tempo de execução, mesmo que as etapas anteriores do cliente são invocadas de forma assíncrona no cliente. O `Multiply` e `Divide` operações são usadas para chamar o serviço de forma assíncrona no lado do serviço, mesmo se o cliente invoca forma síncrona. Este exemplo define o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> propriedade para `true`. Essa configuração de propriedade, em combinação com a implementação do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] padrão assíncrono, informa ao tempo de execução para invocar a operação de forma assíncrona.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
