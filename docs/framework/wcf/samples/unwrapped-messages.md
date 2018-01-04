---
title: Mensagens sem quebra de texto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6014ee5fa7f714340f7069e5b5d39e6b4146dbb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="unwrapped-messages"></a><span data-ttu-id="45262-102">Mensagens sem quebra de texto</span><span class="sxs-lookup"><span data-stu-id="45262-102">Unwrapped Messages</span></span>
<span data-ttu-id="45262-103">Este exemplo demonstra mensagens sem.</span><span class="sxs-lookup"><span data-stu-id="45262-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="45262-104">Por padrão, o corpo da mensagem é formatado, de modo que os parâmetros para uma operação de serviço são quebrados.</span><span class="sxs-lookup"><span data-stu-id="45262-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="45262-105">O exemplo a seguir mostra um `Add` mensagem de solicitação para o `ICalculator` serviço no modo encapsulado.</span><span class="sxs-lookup"><span data-stu-id="45262-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
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
  
 <span data-ttu-id="45262-106">O `<Add>` elemento no corpo da mensagem encapsula o `n1` e `n2` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="45262-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="45262-107">Em contraste, o exemplo a seguir mostra a mensagem equivalente no modo não encapsulado.</span><span class="sxs-lookup"><span data-stu-id="45262-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="45262-108">A mensagem não encapsulada não estiver disposto a `n1` e `n2` parâmetros em um elemento que contém, eles são filhos diretos do elemento de corpo soap.</span><span class="sxs-lookup"><span data-stu-id="45262-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45262-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="45262-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45262-110">Neste exemplo, uma mensagem desencapsulamento é criada aplicando o <xref:System.ServiceModel.MessageContractAttribute> para o tipo de parâmetro de operação de serviço e o tipo de valor de retorno, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="45262-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="45262-111">Para permitir que você veja as mensagens que estão sendo enviados e recebidos, este exemplo usa o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="45262-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="45262-112">Além disso, o <xref:System.ServiceModel.WSHttpBinding> foi configurado sem segurança, para reduzir o número de mensagens que ele registra.</span><span class="sxs-lookup"><span data-stu-id="45262-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="45262-113">O log de rastreamento resultante (c:\logs\Message.log) pode ser exibido usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="45262-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="45262-114">Para exibir o conteúdo da mensagem, selecione **mensagens** à esquerda e os painéis à direita da ferramenta do Visualizador de rastreamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="45262-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="45262-115">Logs de rastreamento neste exemplo são configurados para ser gerado para a pasta c:\Logs.</span><span class="sxs-lookup"><span data-stu-id="45262-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="45262-116">Criar essa pasta antes de executar o exemplo e conceder ao usuário permissões para este diretório de gravação do serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="45262-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45262-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="45262-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45262-118">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45262-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="45262-119">Crie um diretório c:\Logs. para mensagens de log.</span><span class="sxs-lookup"><span data-stu-id="45262-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="45262-120">Conceda ao usuário permissões para este diretório de gravação do serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="45262-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="45262-121">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45262-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="45262-122">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45262-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45262-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="45262-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45262-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="45262-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45262-125">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="45262-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45262-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="45262-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="45262-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45262-127">See Also</span></span>
