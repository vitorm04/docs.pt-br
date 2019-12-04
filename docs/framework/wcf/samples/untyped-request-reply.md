---
title: Solicitação-resposta não tipada
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: ba1caddd8f37a37df63e2710883f3096e0989fcd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715860"
---
# <a name="untyped-requestreply"></a>Solicitações/Respostas não digitadas
Este exemplo demonstra como definir contratos de operação que usam a classe Message.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O contrato de serviço define uma operação que usa um tipo de mensagem como um argumento e retorna uma mensagem. A operação coleta todos os dados necessários para calcular a soma do corpo da mensagem e, em seguida, envia a soma como corpo na mensagem de retorno.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 No serviço, a operação recupera a matriz de inteiros passada na mensagem de entrada e, em seguida, computa a soma. Para enviar uma mensagem de resposta, o exemplo cria uma nova mensagem com a versão e a ação da mensagem apropriada e adiciona a soma computada como seu corpo. O código de exemplo a seguir demonstra isso.  
  
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
  
 O cliente usa o código gerado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um proxy para o serviço remoto. Para enviar uma mensagem de solicitação, o cliente deve ter a versão da mensagem, que depende do canal subjacente. Portanto, ele cria um novo <xref:System.ServiceModel.OperationContextScope> com escopo definido para o canal de proxy criado, que cria um <xref:System.ServiceModel.OperationContext> com a versão de mensagem correta populada em sua propriedade `OutgoingMessageHeaders.MessageVersion`. O cliente passa uma matriz de entrada como o corpo para a mensagem de solicitação e, em seguida, invoca o `ComputeSum` no proxy. Em seguida, o cliente recupera a soma das entradas passadas acessando o método `GetBody<T>` na mensagem de resposta. O código de exemplo a seguir demonstra isso.  
  
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
  
 Este exemplo é um exemplo hospedado na Web e, portanto, somente o executável do cliente deve ser executado. A seguir está a saída de exemplo no cliente.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Este exemplo é um exemplo hospedado na Web e, portanto, verifique o link fornecido na etapa 3 para ver como criar e executar o exemplo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
