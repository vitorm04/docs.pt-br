---
title: Sem tipo de solicitação-resposta
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 2eb6a46d339c9277c1622c0cc16d057b186f1d79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612743"
---
# <a name="untyped-requestreply"></a>Solicitações/Respostas não digitadas
Este exemplo demonstra como definir contratos de operação que usam a classe de mensagem.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md). O contrato de serviço define uma única operação que usa um tipo de mensagem como um argumento e retorna uma mensagem. A operação de coleta todos os dados necessários para calcular a soma do corpo da mensagem e, em seguida, envia a soma como o corpo da mensagem de retorno.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 No serviço, a operação recupera a matriz de inteiros passada na mensagem de entrada e, em seguida, calcula a soma. Para enviar uma mensagem de resposta, o exemplo cria uma nova mensagem com a versão de mensagem apropriado e a ação e adiciona a soma calculada como seu corpo. O código de exemplo a seguir demonstra isso.  
  
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
  
 O cliente usa o código que é gerado pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um proxy para o serviço remoto. Para enviar uma mensagem de solicitação, o cliente deve ter a versão de mensagem, que depende do canal subjacente. Portanto, ele cria um novo <xref:System.ServiceModel.OperationContextScope> com escopo para o canal de proxy criado por ele, que cria um <xref:System.ServiceModel.OperationContext> com a versão correta da mensagem preenchida no seu `OutgoingMessageHeaders.MessageVersion` propriedade. O cliente passa uma matriz de entrada como o corpo para a mensagem de solicitação e, em seguida, invoca o `ComputeSum` no proxy. O cliente, em seguida, recupera a soma das entradas que ele passado, acessando o `GetBody<T>` método na mensagem de resposta. O código de exemplo a seguir demonstra isso.  
  
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
  
 Este exemplo é um exemplo hospedado na Web e para que somente o executável do cliente deve ser executado. A seguir está a saída de exemplo no cliente.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Este exemplo é um exemplo hospedado na Web e portanto, verifique o link fornecido na etapa 3 para ver como criar e executar o exemplo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Consulte também
