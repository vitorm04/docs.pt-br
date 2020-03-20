---
title: Configuração simplificada para serviços do WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183348"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="27ee7-102">Configuração simplificada para serviços do WCF</span><span class="sxs-lookup"><span data-stu-id="27ee7-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="27ee7-103">Esta amostra demonstra como implementar e configurar um serviço e cliente típico usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="27ee7-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="27ee7-104">Esta amostra é a base para todas as outras amostras de tecnologia básica.</span><span class="sxs-lookup"><span data-stu-id="27ee7-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="27ee7-105">Este serviço, que expõe um ponto final para se comunicar com o serviço, usa a configuração simplificada no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="27ee7-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="27ee7-106">Antes do .NET Framework 4, o ponto final é normalmente definido em um arquivo de configuração (Web.config), como mostrado no código de configuração do exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="27ee7-106">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="27ee7-107">No Quadro .NET `<service>` 4, o elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="27ee7-107">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="27ee7-108">Quando um serviço não define nenhum ponto final, um ponto final para cada endereço base e contrato implementado são adicionados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="27ee7-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="27ee7-109">O endereço base é anexado ao nome do contrato para determinar o ponto final e a vinculação é determinada pelo esquema de endereço.</span><span class="sxs-lookup"><span data-stu-id="27ee7-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="27ee7-110">O exemplo de código a seguir demonstra um arquivo de configuração simplificado.</span><span class="sxs-lookup"><span data-stu-id="27ee7-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="27ee7-111">Conforme configurado, o serviço pode `http://localhost/servicemodelsamples/service.svc` ser acessado por um cliente no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="27ee7-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="27ee7-112">Para clientes em computadores remotos acessarem o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de host local.</span><span class="sxs-lookup"><span data-stu-id="27ee7-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="27ee7-113">O serviço não expõe metadados por padrão.</span><span class="sxs-lookup"><span data-stu-id="27ee7-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="27ee7-114">Como tal, o serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> se volta contra o comportamento.</span><span class="sxs-lookup"><span data-stu-id="27ee7-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="27ee7-115">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="27ee7-115">To use this sample</span></span>  
  
1. <span data-ttu-id="27ee7-116">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27ee7-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="27ee7-117">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27ee7-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="27ee7-118">Execute a amostra seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="27ee7-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="27ee7-119">Clique com o botão direito do mouse no projeto **Serviço** e selecione **Set as StartUp project**e pressione **Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="27ee7-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="27ee7-120">Aguarde a saída do console confirmando que o serviço está em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="27ee7-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="27ee7-121">Clique com o botão direito do **mouse** no projeto Cliente e selecione **Set as StartUp project**e pressione **Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="27ee7-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="27ee7-122">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="27ee7-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="27ee7-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="27ee7-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="27ee7-124">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="27ee7-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27ee7-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="27ee7-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="27ee7-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="27ee7-126">See also</span></span>

- <span data-ttu-id="27ee7-127">[Amostras de gerenciamento de appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="27ee7-127">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="27ee7-128">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="27ee7-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
