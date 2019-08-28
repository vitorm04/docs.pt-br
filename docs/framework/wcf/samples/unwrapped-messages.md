---
title: Mensagens sem quebra de texto
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 9609160885a46d76c5df54538fc088a3d025ca3b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044614"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="9ecaf-102">Mensagens sem quebra de texto</span><span class="sxs-lookup"><span data-stu-id="9ecaf-102">Unwrapped Messages</span></span>
<span data-ttu-id="9ecaf-103">Este exemplo demonstra mensagens não encapsuladas.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="9ecaf-104">Por padrão, o corpo da mensagem é formatado de modo que os parâmetros para uma operação de serviço sejam encapsulados.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="9ecaf-105">O exemplo a seguir mostra `Add` uma mensagem de solicitação `ICalculator` para o serviço no modo encapsulado.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="9ecaf-106">O `<Add>` elemento no corpo da mensagem encapsula os `n1` parâmetros e `n2` .</span><span class="sxs-lookup"><span data-stu-id="9ecaf-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="9ecaf-107">Por outro lado, o exemplo a seguir mostra a mensagem equivalente no modo não encapsulado.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="9ecaf-108">A mensagem desencapsulada não encapsula os `n1` parâmetros `n2` e em um elemento contentor, eles são filhos diretos do elemento body do SOAP.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecaf-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9ecaf-110">Neste exemplo, uma mensagem desencapsulada é criada aplicando o <xref:System.ServiceModel.MessageContractAttribute> ao tipo de parâmetro de operação de serviço e o tipo de valor de retorno, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="9ecaf-111">Para permitir que você veja as mensagens que estão sendo enviadas e recebidas, este exemplo usa o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="9ecaf-112">Além disso, o <xref:System.ServiceModel.WSHttpBinding> foi configurado sem segurança, para reduzir o número de mensagens que ele registra.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="9ecaf-113">O log de rastreamento resultante (c:\logs\Message.log) pode ser exibido usando a [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9ecaf-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="9ecaf-114">Para exibir o conteúdo da mensagem, selecione **mensagens** nos painéis esquerdo e direito da ferramenta Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="9ecaf-115">Os logs de rastreamento neste exemplo são configurados para serem gerados na pasta C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="9ecaf-116">Crie essa pasta antes de executar o exemplo e conceda ao serviço de rede do usuário permissões de gravação para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ecaf-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9ecaf-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9ecaf-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ecaf-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9ecaf-119">Crie um diretório do C:\LOGS para mensagens de log.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="9ecaf-120">Conceda permissões de gravação ao serviço de rede do usuário para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="9ecaf-121">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ecaf-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="9ecaf-122">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ecaf-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9ecaf-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ecaf-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-124">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9ecaf-125">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ecaf-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9ecaf-126">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
