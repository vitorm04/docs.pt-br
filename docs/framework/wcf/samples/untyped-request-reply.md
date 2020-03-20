---
title: Solicitação-Resposta não digitada
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: a526837b9bccf7a6287972e482a189a53ecadaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183281"
---
# <a name="untyped-requestreply"></a>Solicitações/Respostas não digitadas
Esta amostra demonstra como definir contratos de operação que usam a classe Mensagem.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). O contrato de serviço define uma operação que leva um tipo de mensagem como argumento e retorna uma mensagem. A operação coleta todos os dados necessários para calcular a soma do corpo de mensagem e, em seguida, envia a soma como corpo na mensagem de retorno.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 No serviço, a operação recupera o conjunto de inteiros passados na mensagem de entrada e, em seguida, calcula a soma. Para enviar uma mensagem de resposta, a amostra cria uma nova mensagem com a versão de mensagem apropriada e Action e adiciona a soma calculada como seu corpo. O seguinte código de amostra demonstra isso.  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 O cliente usa o código gerado pelo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um proxy para o serviço remoto. Para enviar uma mensagem de solicitação, o cliente deve ter a versão da mensagem, que depende do canal subjacente. Assim, ele cria <xref:System.ServiceModel.OperationContextScope> um novo escopo para o canal <xref:System.ServiceModel.OperationContext> proxy que criou, que `OutgoingMessageHeaders.MessageVersion` cria uma versão de mensagem correta povoada em sua propriedade. O cliente passa uma matriz de entrada como o `ComputeSum` corpo para a mensagem de solicitação e, em seguida, invoca o no proxy. Em seguida, o cliente recupera a soma das entradas que passou acessando o `GetBody<T>` método na mensagem de resposta. O seguinte código de amostra demonstra isso.  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",
                                                       response);  
}  
```  
  
 Esta amostra é uma amostra hospedada na Web e, portanto, apenas o executável do cliente deve ser executado. A seguir está a saída de amostra no cliente.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Esta amostra é uma amostra hospedada na Web e, portanto, verifique o link fornecido na etapa 3 para ver como construir e executar a amostra.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
