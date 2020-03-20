---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: da54a835fd32efe4f53a80701465d2d7d8adba7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183473"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="b8b89-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="b8b89-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="b8b89-103">Esta amostra `netNamedPipeBinding` demonstra a vinculação, que fornece comunicação entre processos na mesma máquina.</span><span class="sxs-lookup"><span data-stu-id="b8b89-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="b8b89-104">Os tubos nomeados não funcionam entre as máquinas.</span><span class="sxs-lookup"><span data-stu-id="b8b89-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="b8b89-105">Esta amostra é baseada no serviço de calculadora [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="b8b89-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="b8b89-106">Nesta amostra, o serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="b8b89-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="b8b89-107">Tanto o cliente quanto o serviço são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="b8b89-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8b89-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b8b89-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8b89-109">A vinculação é especificada nos arquivos de configuração para o cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="b8b89-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b8b89-110">O tipo de vinculação `binding` é especificado no atributo do [ \<ponto final>](../../configure-apps/file-schema/wcf/endpoint-element.md) ou [ \<> de ponto final do \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elemento>cliente, conforme mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="b8b89-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b8b89-111">A amostra anterior mostra como configurar um `netNamedPipeBinding` ponto final para usar a vinculação com as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="b8b89-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="b8b89-112">Se você quiser configurar `netNamedPipeBinding` a vinculação e alterar algumas de suas configurações, você deve definir uma configuração de vinculação.</span><span class="sxs-lookup"><span data-stu-id="b8b89-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="b8b89-113">O ponto final deve fazer referência `bindingConfiguration` à configuração de vinculação por nome com um atributo.</span><span class="sxs-lookup"><span data-stu-id="b8b89-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b8b89-114">Nesta amostra, a configuração `Binding1` de vinculação é nomeada e tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="b8b89-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
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
  
 <span data-ttu-id="b8b89-115">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="b8b89-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b8b89-116">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b8b89-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8b89-117">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b8b89-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b8b89-118">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8b89-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b8b89-119">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8b89-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b8b89-120">Para executar a amostra em uma única configuração de máquina, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8b89-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b8b89-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b8b89-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8b89-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b8b89-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b8b89-123">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b8b89-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8b89-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b8b89-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
