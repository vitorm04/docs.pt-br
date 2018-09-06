---
title: Como configurar um cliente básico do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 2866cbd5862bf55286fc771823488cf913863de2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855849"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="d7445-102">Como configurar um cliente básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d7445-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="d7445-103">Esse é o quinto de seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d7445-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="d7445-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d7445-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="d7445-105">Este tópico discute o arquivo de configuração de cliente que foi gerado usando a funcionalidade Adicionar referência de serviço do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ou o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d7445-105">This topic discusses the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d7445-106">Configurando o cliente consiste em especificar o ponto de extremidade que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d7445-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="d7445-107">Um ponto de extremidade tem um endereço, uma ligação e um contrato, e cada um deles deve ser especificada no processo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="d7445-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="d7445-108">Para configurar um cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d7445-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="d7445-109">Abra o arquivo de configuração gerado (App. config) do projeto GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="d7445-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="d7445-110">O exemplo a seguir é um modo de exibição do arquivo de configuração gerado.</span><span class="sxs-lookup"><span data-stu-id="d7445-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="d7445-111">Sob o [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, localize o [ \<ponto de extremidade >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.</span><span class="sxs-lookup"><span data-stu-id="d7445-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="d7445-112">Este exemplo configura o ponto de extremidade que o cliente usa para acessar o serviço que está localizado no seguinte endereço: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span><span class="sxs-lookup"><span data-stu-id="d7445-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="d7445-113">O elemento de ponto de extremidade Especifica que o `ServiceReference1.ICalculator` contrato de serviço é usado para comunicação entre o cliente do WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d7445-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="d7445-114">O canal do WCF é configurado com o sistema forneceu <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d7445-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="d7445-115">Esse contrato foi gerado por meio de adicionar referência de serviço no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7445-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="d7445-116">Ele é essencialmente uma cópia do contrato que foi definido no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="d7445-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="d7445-117">O <xref:System.ServiceModel.WSHttpBinding> associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7445-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  <span data-ttu-id="d7445-118">Para obter mais informações sobre como usar o cliente gerado com essa configuração, consulte [como: usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d7445-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7445-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7445-119">See Also</span></span>  
 [<span data-ttu-id="d7445-120">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d7445-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="d7445-121">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d7445-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="d7445-122">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="d7445-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="d7445-123">Introdução</span><span class="sxs-lookup"><span data-stu-id="d7445-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="d7445-124">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="d7445-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
