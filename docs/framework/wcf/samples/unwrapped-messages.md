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
# <a name="unwrapped-messages"></a><span data-ttu-id="51ea5-102">Mensagens sem quebra de texto</span><span class="sxs-lookup"><span data-stu-id="51ea5-102">Unwrapped Messages</span></span>
<span data-ttu-id="51ea5-103">Esta amostra demonstra mensagens desembrulhadas.</span><span class="sxs-lookup"><span data-stu-id="51ea5-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="51ea5-104">Por padrão, o corpo da mensagem é formatado de modo que os parâmetros de uma operação de serviço sejam embrulhados.</span><span class="sxs-lookup"><span data-stu-id="51ea5-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="51ea5-105">A amostra a `Add` seguir mostra `ICalculator` uma mensagem de solicitação para o serviço no modo embrulhado.</span><span class="sxs-lookup"><span data-stu-id="51ea5-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="51ea5-106">O `<Add>` elemento no corpo da `n1` `n2` mensagem envolve os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="51ea5-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="51ea5-107">Em contraste, a amostra a seguir mostra a mensagem equivalente no modo desembrulhado.</span><span class="sxs-lookup"><span data-stu-id="51ea5-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="51ea5-108">A mensagem desembrulhada não envolve os `n1` parâmetros e `n2` parâmetros em um elemento contendo, eles são filhos diretos do elemento corpo sabão.</span><span class="sxs-lookup"><span data-stu-id="51ea5-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51ea5-109">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="51ea5-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="51ea5-110">Nesta amostra, uma mensagem desembrulhada <xref:System.ServiceModel.MessageContractAttribute> é criada aplicando-se o tipo de parâmetro de operação de serviço e o tipo de valor de retorno, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="51ea5-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="51ea5-111">Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, esta amostra usa rastreamento.</span><span class="sxs-lookup"><span data-stu-id="51ea5-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="51ea5-112">Além disso, <xref:System.ServiceModel.WSHttpBinding> o foi configurado sem segurança, para reduzir o número de mensagens que registra.</span><span class="sxs-lookup"><span data-stu-id="51ea5-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="51ea5-113">O registro de rastreamento resultante (c:\logs\Message.log) pode ser visualizado usando a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="51ea5-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="51ea5-114">Para exibir o conteúdo da mensagem, selecione **Mensagens** nos painéis esquerdo e direito da ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="51ea5-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="51ea5-115">Os registros de rastreamento nesta amostra são configurados para serem gerados na pasta C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="51ea5-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="51ea5-116">Crie esta pasta antes de executar a amostra e dê ao usuário permissões de gravação do Serviço de Rede para este diretório.</span><span class="sxs-lookup"><span data-stu-id="51ea5-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51ea5-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="51ea5-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="51ea5-118">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51ea5-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="51ea5-119">Crie um diretório C:\LOGS para registrar mensagens.</span><span class="sxs-lookup"><span data-stu-id="51ea5-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="51ea5-120">Dê ao usuário permissões de gravação do Serviço de Rede para este diretório.</span><span class="sxs-lookup"><span data-stu-id="51ea5-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="51ea5-121">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51ea5-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="51ea5-122">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51ea5-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="51ea5-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="51ea5-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51ea5-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="51ea5-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="51ea5-125">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="51ea5-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51ea5-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="51ea5-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
