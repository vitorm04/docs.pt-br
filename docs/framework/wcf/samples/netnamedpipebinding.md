---
title: NetNamedPipeBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ba6c85bbee3a0740568b47ea1a54db1a4327743f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="ce6db-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="ce6db-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="ce6db-103">Este exemplo demonstra o `netNamedPipeBinding` associação, que fornece comunicação entre processos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="ce6db-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="ce6db-104">Pipes nomeados não funcionam em computadores.</span><span class="sxs-lookup"><span data-stu-id="ce6db-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="ce6db-105">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) serviço da Calculadora.</span><span class="sxs-lookup"><span data-stu-id="ce6db-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="ce6db-106">Neste exemplo, o serviço é hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ce6db-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="ce6db-107">O cliente e o serviço são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="ce6db-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce6db-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ce6db-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce6db-109">A associação é especificada nos arquivos de configuração do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce6db-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="ce6db-110">O tipo de associação é especificado no `binding` atributo do[\<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento conforme mostrado no exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="ce6db-110">The binding type is specified in the `binding` attribute of the[\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="ce6db-111">O exemplo anterior mostra como configurar um ponto de extremidade para usar o `netNamedPipeBinding` associação com as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="ce6db-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="ce6db-112">Se você deseja configurar o `netNamedPipeBinding` de associação e alterar algumas de suas configurações, você deve definir uma configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="ce6db-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="ce6db-113">O ponto de extremidade deve fazer referência a configuração de associação por nome com um `bindingConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="ce6db-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="ce6db-114">Neste exemplo, a configuração de associação é denominada `Binding1` e tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="ce6db-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"   
             maxConnections="10"   
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ce6db-115">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ce6db-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ce6db-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ce6db-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce6db-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ce6db-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ce6db-118">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce6db-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ce6db-119">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce6db-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ce6db-120">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ce6db-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce6db-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ce6db-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce6db-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ce6db-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ce6db-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ce6db-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce6db-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ce6db-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
  
## <a name="see-also"></a><span data-ttu-id="ce6db-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce6db-125">See Also</span></span>
