---
title: Configuração simplificada para serviços do WCF
description: Saiba como implementar e configurar um serviço e cliente típicos usando o WCF. O serviço se comunica usando um ponto de extremidade especificado em um arquivo de configuração.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: dd05754dcfe36cb2e9c28ce20a5927585f85478f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554261"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="ec123-104">Configuração simplificada para serviços do WCF</span><span class="sxs-lookup"><span data-stu-id="ec123-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="ec123-105">Este exemplo demonstra como implementar e configurar um serviço e cliente típicos usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ec123-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ec123-106">Este exemplo é a base para todos os outros exemplos de tecnologia básica.</span><span class="sxs-lookup"><span data-stu-id="ec123-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="ec123-107">Esse serviço, que expõe um ponto de extremidade para se comunicar com o serviço, usa a configuração simplificada no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec123-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="ec123-108">Antes do .NET Framework 4, o ponto de extremidade normalmente é definido em um arquivo de configuração (Web.config), conforme mostrado no código de configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec123-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="ec123-109">No .NET Framework 4, o `<service>` elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="ec123-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="ec123-110">Quando um serviço não define nenhum ponto de extremidade, um ponto de extremidades para cada endereço base e contrato implementado é adicionado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="ec123-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="ec123-111">O endereço base é acrescentado ao nome do contrato para determinar o ponto de extremidade e a associação é determinada pelo esquema de endereço.</span><span class="sxs-lookup"><span data-stu-id="ec123-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="ec123-112">O exemplo de código a seguir demonstra um arquivo de configuração simplificado.</span><span class="sxs-lookup"><span data-stu-id="ec123-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="ec123-113">Conforme configurado, o serviço pode ser acessado pelo `http://localhost/servicemodelsamples/service.svc` cliente do no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="ec123-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="ec123-114">Para clientes em computadores remotos acessarem o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="ec123-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="ec123-115">O serviço não expõe metadados por padrão.</span><span class="sxs-lookup"><span data-stu-id="ec123-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="ec123-116">Como tal, o serviço ativa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.</span><span class="sxs-lookup"><span data-stu-id="ec123-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="ec123-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="ec123-117">To use this sample</span></span>  
  
1. <span data-ttu-id="ec123-118">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ec123-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ec123-119">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ec123-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ec123-120">Execute o exemplo seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ec123-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="ec123-121">Clique com o botão direito do mouse no projeto de **serviço** e selecione **definir como projeto de inicialização**e pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ec123-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="ec123-122">Aguarde a saída do console confirmando se o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="ec123-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="ec123-123">Clique com o botão direito do mouse no projeto **cliente** e selecione **definir como projeto de inicialização**e pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="ec123-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec123-124">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ec123-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ec123-125">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ec123-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ec123-126">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ec123-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ec123-127">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ec123-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="ec123-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec123-128">See also</span></span>

- <span data-ttu-id="ec123-129">[Exemplos de gerenciamento do AppFabric](/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ec123-129">[AppFabric Management Samples](/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="ec123-130">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="ec123-130">Simplified Configuration</span></span>](../simplified-configuration.md)
