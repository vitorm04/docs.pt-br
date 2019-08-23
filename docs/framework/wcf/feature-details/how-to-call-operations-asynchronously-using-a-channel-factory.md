---
title: 'Como: chamar operações assíncronas usando uma fábrica de canais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 3080514d06119a2f1b621cff16056ac7577c30b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966812"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Como: chamar operações assíncronas usando uma fábrica de canais
Este tópico aborda como um cliente pode acessar uma operação de serviço de forma assíncrona ao usar um aplicativo cliente baseado em um <xref:System.ServiceModel.ChannelFactory%601>. (Ao usar um <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objeto para invocar um serviço, você pode usar o modelo de chamada assíncrona orientado por evento. Para obter mais informações, confira [Como: Chamar operações de serviço](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)de forma assíncrona. Para obter mais informações sobre o modelo de chamada assíncrona baseado em evento, consulte [padrão assíncrono baseado em evento (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 O serviço neste tópico implementa a `ICalculator` interface. O cliente pode chamar as operações nessa interface de forma assíncrona, o que significa `Add` que as operações como são divididas `EndAdd`em dois métodos, `BeginAdd` e o primeiro deles inicia a chamada e a última que recupera o resultado Quando a operação for concluída. Para obter um exemplo que mostra como implementar uma operação de forma assíncrona em [um serviço, consulte Como: Implemente uma operação](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)de serviço assíncrona. Para obter detalhes sobre as operações síncronas e assíncronas, consulte operações síncronas [e](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)assíncronas.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Para chamar operações do serviço WCF de forma assíncrona  
  
1. Execute a ferramenta [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com a `/async` opção conforme mostrado no comando a seguir.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Isso gera uma versão de cliente assíncrona do contrato de serviço para a operação.  
  
2. Crie uma função de retorno de chamada a ser chamada quando a operação assíncrona for concluída, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Para acessar uma operação de serviço de forma assíncrona, crie o `Begin[Operation]` cliente e chame o `BeginAdd`(por exemplo,) e especifique uma função de retorno de chamada, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Quando a função de retorno de chamada é executada, `End<operation>` o cliente chama ( `EndAdd`por exemplo,) para recuperar o resultado.  
  
## <a name="example"></a>Exemplo  
 O serviço usado com o código do cliente que é usado no procedimento anterior implementa a `ICalculator` interface, conforme mostrado no código a seguir. No lado do serviço, as `Add` operações `Subtract` e do contrato são invocadas de forma síncrona pelo tempo de execução do Windows Communication Foundation (WCF), mesmo que as etapas do cliente precedentes sejam invocadas de modo assíncrono no cliente. As `Multiply` operações `Divide` e são usadas para invocar o serviço de forma assíncrona no lado do serviço, mesmo que o cliente os invoque de maneira síncrona. Este exemplo define a <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> Propriedade como `true`. Essa configuração de propriedade, em combinação com a implementação do padrão .NET Framework assíncrono, informa o tempo de execução para invocar a operação de forma assíncrona.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
