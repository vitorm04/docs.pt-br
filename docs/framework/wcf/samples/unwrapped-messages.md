---
title: Mensagens sem quebra de texto
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 6fc535a9d7126fa1a6e41fad474b204cf0036c62
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951491"
---
# <a name="unwrapped-messages"></a>Mensagens sem quebra de texto
Este exemplo demonstra mensagens não encapsuladas. Por padrão, o corpo da mensagem é formatado de modo que os parâmetros para uma operação de serviço sejam encapsulados. O exemplo a seguir mostra `Add` uma mensagem de solicitação `ICalculator` para o serviço no modo encapsulado.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 O `<Add>` elemento no corpo da mensagem encapsula os `n1` parâmetros e `n2` . Por outro lado, o exemplo a seguir mostra a mensagem equivalente no modo não encapsulado.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 A mensagem desencapsulada não encapsula os `n1` parâmetros `n2` e em um elemento contentor, eles são filhos diretos do elemento body do SOAP.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Neste exemplo, uma mensagem desencapsulada é criada aplicando o <xref:System.ServiceModel.MessageContractAttribute> ao tipo de parâmetro de operação de serviço e o tipo de valor de retorno, conforme mostrado no código de exemplo a seguir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, este exemplo usa o rastreamento. Além disso, o <xref:System.ServiceModel.WSHttpBinding> foi configurado sem segurança, para reduzir o número de mensagens que ele registra.  
  
 O log de rastreamento resultante (c:\logs\Message.log) pode ser exibido usando a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Para exibir o conteúdo da mensagem, selecione **mensagens** nos painéis esquerdo e direito da ferramenta Visualizador de rastreamento de serviço. Os logs de rastreamento neste exemplo são configurados para serem gerados na pasta C:\LOGS. Crie essa pasta antes de executar o exemplo e conceda ao serviço de rede do usuário permissões de gravação para esse diretório.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Crie um diretório do C:\LOGS para mensagens de log. Conceda permissões de gravação ao serviço de rede do usuário para esse diretório.  
  
3. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
