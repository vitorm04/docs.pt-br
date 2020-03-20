---
title: Mensagens sem quebra de texto
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 81592910d8530cea2df5ec1fd8a8b1145350ef78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143727"
---
# <a name="unwrapped-messages"></a>Mensagens sem quebra de texto
Esta amostra demonstra mensagens desembrulhadas. Por padrão, o corpo da mensagem é formatado de modo que os parâmetros de uma operação de serviço sejam embrulhados. A amostra a `Add` seguir mostra `ICalculator` uma mensagem de solicitação para o serviço no modo embrulhado.  
  
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
  
 O `<Add>` elemento no corpo da `n1` `n2` mensagem envolve os parâmetros. Em contraste, a amostra a seguir mostra a mensagem equivalente no modo desembrulhado.  
  
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
  
 A mensagem desembrulhada não envolve os `n1` parâmetros e `n2` parâmetros em um elemento contendo, eles são filhos diretos do elemento corpo sabão.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Nesta amostra, uma mensagem desembrulhada <xref:System.ServiceModel.MessageContractAttribute> é criada aplicando-se o tipo de parâmetro de operação de serviço e o tipo de valor de retorno, conforme mostrado no código de amostra a seguir.  
  
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
  
 Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, esta amostra usa rastreamento. Além disso, <xref:System.ServiceModel.WSHttpBinding> o foi configurado sem segurança, para reduzir o número de mensagens que registra.  
  
 O registro de rastreamento resultante (c:\logs\Message.log) pode ser visualizado usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Para exibir o conteúdo da mensagem, selecione **Mensagens** nos painéis esquerdo e direito da ferramenta Visualizador de rastreamento de serviço. Os registros de rastreamento nesta amostra são configurados para serem gerados na pasta C:\LOGS. Crie esta pasta antes de executar a amostra e dê ao usuário permissões de gravação do Serviço de Rede para este diretório.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Crie um diretório C:\LOGS para registrar mensagens. Dê ao usuário permissões de gravação do Serviço de Rede para este diretório.  
  
3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
