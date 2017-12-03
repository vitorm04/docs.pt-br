---
title: "Sem tipo solicitação-resposta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45e68bd28a4ab5a0e7425bf06b02b8c3d3d25311
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="untyped-requestreply"></a>Solicitações/Respostas não digitadas
Este exemplo demonstra como definir contratos de operação que usam a classe de mensagem.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O contrato de serviço define uma operação que usa um tipo de mensagem como um argumento e retorna uma mensagem. A operação de coleta todos os dados necessários para calcular a soma do corpo da mensagem e, em seguida, envia a soma como corpo da mensagem de retorno.  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Sobre o serviço, a operação recupera a matriz de inteiros passado na mensagem de entrada e, em seguida, calcula a soma. Para enviar uma mensagem de resposta, o exemplo cria uma nova mensagem com a versão de mensagem apropriado e a ação e adiciona a soma calculada como seu corpo. O código de exemplo a seguir demonstra isso.  
  
```  
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
  
 O cliente usa o código que é gerado por [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um proxy para o serviço remoto. Para enviar uma mensagem de solicitação, o cliente deve ter a versão de mensagem, que depende do canal subjacente. Assim, ele cria um novo <xref:System.ServiceModel.OperationContextScope> com escopo para o canal de proxy criado por ele, que cria um <xref:System.ServiceModel.OperationContext> com a versão de mensagem correto preenchida no seu `OutgoingMessageHeaders.MessageVersion` propriedade. O cliente passa uma matriz de entrada como o corpo da mensagem de solicitação e, em seguida, invoca o `ComputeSum` no proxy. O cliente recupera a soma das entradas que transmitido acessando o `GetBody<T>` método na mensagem de resposta. O código de exemplo a seguir demonstra isso.  
  
```  
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
  
 Este exemplo é um exemplo de Web hospedada e deve ser executado para que somente o executável do cliente. A seguir está a saída de exemplo no cliente.  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Este exemplo é um exemplo da Web hospedado e por isso, verifique o link fornecido na etapa 3 para saber como criar e executar o exemplo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Consulte também
