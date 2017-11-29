---
title: "Como chamar operações assíncronas usando uma fábrica de canais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c907ed4c5c8cc76899d4f785ef1abf5a2821274f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Como chamar operações assíncronas usando uma fábrica de canais
Este tópico aborda como um cliente pode acessar uma operação de serviço assíncrona usando um <xref:System.ServiceModel.ChannelFactory%601>-com base em aplicativos cliente. (Ao usar um <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objeto invocar um serviço que você pode usar o modelo de chamada assíncrono controlada por evento. Para obter mais informações, consulte [como: chamar operações de serviço assíncrona](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Para obter mais informações sobre o modelo de chamada assíncrono baseado em evento, consulte [programação Multithreaded com o padrão assíncrono baseado em evento](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)  
  
 O serviço neste tópico implementa o `ICalculator` interface. O cliente pode chamar as operações nesta interface de forma assíncrona, o que significa que as operações como `Add` são divididas em dois métodos, `BeginAdd` e `EndAdd`, o primeiro deles inicia a chamada e o último recupera o resultado Quando a operação for concluída. Para obter um exemplo mostrando como implementar uma operação assíncrona em um serviço, consulte [como: implementar uma operação assíncrona do serviço](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Para obter detalhes sobre operações síncronas e assíncronas, consulte [síncrona e operações assíncronas](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>Para chamar operações de serviço WCF de forma assíncrona  
  
1.  Execute o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta com o `/async` opção conforme mostrado no comando a seguir.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Isso gera uma versão de cliente assíncrono do contrato de serviço para a operação.  
  
2.  Crie uma função de retorno de chamada a ser chamado quando a operação assíncrona é concluída, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  Para acessar uma operação de serviço de forma assíncrona, criar o cliente e chamar o `Begin[Operation]` (por exemplo, `BeginAdd`) e especifique uma função de retorno de chamada, conforme mostrado no código de exemplo a seguir.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Quando a função de retorno de chamada é executado, o cliente chama `End<operation>` (por exemplo, `EndAdd`) para recuperar o resultado.  
  
## <a name="example"></a>Exemplo  
 O serviço que é usado com o código de cliente que é usado no procedimento anterior implementa o `ICalculator` interface conforme mostrado no código a seguir. No lado do serviço, o `Add` e `Subtract` operações do contrato são chamadas de forma síncrona pelo [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tempo de execução, mesmo que as etapas anteriores do cliente são chamadas de maneira assíncrona no cliente. O `Multiply` e `Divide` operações são usadas para chamar o serviço de forma assíncrona no lado do serviço, mesmo se o cliente chama sincronicamente. Este exemplo define o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> propriedade `true`. Essa configuração de propriedade, em combinação com a implementação de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] padrão assíncrono, indica o tempo de execução para invocar a operação assíncrona.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Contrato de serviço: Exemplo de assíncrono](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7)
