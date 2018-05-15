---
title: Configuração simplificada para serviços do WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 80e2ac83ec0e07176d6afe6d34c63fb4d8e836d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="bfd03-102">Configuração simplificada para serviços do WCF</span><span class="sxs-lookup"><span data-stu-id="bfd03-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="bfd03-103">Este exemplo demonstra como implementar e configurar um serviço típico e o cliente usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bfd03-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bfd03-104">Este exemplo é a base para todos os outros exemplos de tecnologia básico.</span><span class="sxs-lookup"><span data-stu-id="bfd03-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="bfd03-105">Esse serviço, que expõe um ponto de extremidade de comunicação com o serviço, usa a configuração simplificada no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfd03-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="bfd03-106">Antes de [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o ponto de extremidade normalmente é definido em um arquivo de configuração (Web. config), conforme mostrado no código de configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfd03-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="bfd03-107">Em [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], o `<service>` elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="bfd03-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="bfd03-108">Quando um serviço não define nenhum ponto de extremidade, um ponto de extremidade para cada endereço de base e o contrato implementado são adicionados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="bfd03-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="bfd03-109">O endereço base é acrescentado ao nome do contrato para determinar o ponto de extremidade e a associação é determinada pelo esquema de endereço.</span><span class="sxs-lookup"><span data-stu-id="bfd03-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="bfd03-110">O exemplo de código a seguir demonstra um arquivo de configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="bfd03-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="bfd03-111">Conforme configurado, o serviço pode ser acessado em http://localhost/servicemodelsamples/service.svc por um cliente no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="bfd03-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="bfd03-112">Para clientes em computadores remotos acessar o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="bfd03-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="bfd03-113">Por padrão, o serviço não expõe metadados.</span><span class="sxs-lookup"><span data-stu-id="bfd03-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="bfd03-114">Como tal, o serviço ativa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento.</span><span class="sxs-lookup"><span data-stu-id="bfd03-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="bfd03-115">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="bfd03-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="bfd03-116">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfd03-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bfd03-117">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfd03-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bfd03-118">Execute o exemplo seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="bfd03-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="bfd03-119">Clique com botão direito do **Service** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="bfd03-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="bfd03-120">Aguarde até que a saída do console confirmando que o serviço está ativo e em execução.</span><span class="sxs-lookup"><span data-stu-id="bfd03-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="bfd03-121">Clique com botão direito do **cliente** do projeto e selecione **definir como projeto de inicialização**, em seguida, pressione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="bfd03-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfd03-122">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bfd03-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bfd03-123">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bfd03-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bfd03-124">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bfd03-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bfd03-125">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bfd03-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="bfd03-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfd03-126">See Also</span></span>  
 [<span data-ttu-id="bfd03-127">Exemplos de gerenciamento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="bfd03-127">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="bfd03-128">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="bfd03-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
