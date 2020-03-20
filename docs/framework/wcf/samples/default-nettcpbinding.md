---
title: NetTcpBinding padrão
ms.date: 03/30/2017
helpviewer_keywords:
- Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
ms.openlocfilehash: 4e4887b73a517c2241cbe84b55909817e2e30a5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144767"
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="4e10e-102">NetTcpBinding padrão</span><span class="sxs-lookup"><span data-stu-id="4e10e-102">Default NetTcpBinding</span></span>
<span data-ttu-id="4e10e-103">Esta amostra demonstra o <xref:System.ServiceModel.NetTcpBinding> uso da ligação.</span><span class="sxs-lookup"><span data-stu-id="4e10e-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="4e10e-104">Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="4e10e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="4e10e-105">Nesta amostra, o serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="4e10e-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="4e10e-106">Tanto o cliente quanto o serviço são aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="4e10e-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e10e-107">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4e10e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4e10e-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4e10e-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e10e-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4e10e-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4e10e-110">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="4e10e-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e10e-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4e10e-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="4e10e-112">A vinculação é especificada nos arquivos de configuração para o cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="4e10e-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4e10e-113">O tipo de vinculação `binding` é especificado no atributo do [ \<](../../configure-apps/file-schema/wcf/endpoint-element.md) elemento>ponto final, conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e10e-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="4e10e-114">A amostra anterior mostra como configurar um `netTcpBinding` ponto final para usar a vinculação com as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="4e10e-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="4e10e-115">Se você quiser configurar `netTcpBinding` a vinculação e alterar algumas de suas configurações, é necessário definir uma configuração de vinculação.</span><span class="sxs-lookup"><span data-stu-id="4e10e-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="4e10e-116">O ponto final deve fazer referência `bindingConfiguration` à configuração de vinculação por nome com um atributo.</span><span class="sxs-lookup"><span data-stu-id="4e10e-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="4e10e-117">Nesta amostra, a configuração `Binding1` de vinculação é nomeada e definida como mostra da configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e10e-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"  
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4e10e-118">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="4e10e-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4e10e-119">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4e10e-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e10e-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4e10e-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e10e-121">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="4e10e-121">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="4e10e-122">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e10e-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="4e10e-123">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e10e-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4e10e-124">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e10e-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4e10e-125">Como o servidor está hospedado em auto-hospedado, você deve especificar uma identidade no arquivo App.config do cliente para executar a amostra em uma configuração de máquina cruzada.</span><span class="sxs-lookup"><span data-stu-id="4e10e-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name=""  
          address="net.tcp://servername:9000/servicemodelsamples/service"
          binding="netTcpBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator">  
            <identity>  
              <userPrincipalName value = "user_name@service_domain"/>  
            </identity>  
      </endpoint>  
    </client>  
    ```  
