---
title: 'Como: Configurar um cliente básico do Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 18acec48b2af78877f99335da38ccb0ae8942824
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332306"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="32a3c-102">Como: Configurar um cliente básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="32a3c-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>

<span data-ttu-id="32a3c-103">Esse é o quinto de seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="32a3c-103">This is the fifth of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="32a3c-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="32a3c-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="32a3c-105">Este tópico discute o arquivo de configuração de cliente que foi gerado usando o **adicionar referência de serviço** funcionalidade do Visual Studio ou o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="32a3c-105">This topic discusses the client configuration file that was generated using the **Add Service Reference** functionality of Visual Studio or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="32a3c-106">Configurando o cliente consiste em especificar o ponto de extremidade que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="32a3c-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="32a3c-107">Um ponto de extremidade tem um endereço, uma ligação e um contrato, e cada um deles deve ser especificada no processo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="32a3c-107">An endpoint has an address, a binding, and a contract, and each of these must be specified in the process of configuring the client.</span></span>

## <a name="configure-a-windows-communication-foundation-client"></a><span data-ttu-id="32a3c-108">Configurar um cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="32a3c-108">Configure a Windows Communication Foundation client</span></span>

<span data-ttu-id="32a3c-109">Abra o arquivo de configuração gerado (App. config) do projeto GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="32a3c-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="32a3c-110">O exemplo a seguir é um modo de exibição do arquivo de configuração gerado.</span><span class="sxs-lookup"><span data-stu-id="32a3c-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="32a3c-111">Sob o [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, localize o [ \<ponto de extremidade >](../configure-apps/file-schema/wcf/endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="32a3c-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span>

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

<span data-ttu-id="32a3c-112">Este exemplo configura o ponto de extremidade que o cliente usa para acessar o serviço que está localizado no seguinte endereço: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="32a3c-112">This example configures the endpoint that the client uses to access the service that is located at the following address: `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`.</span></span>

<span data-ttu-id="32a3c-113">O elemento de ponto de extremidade Especifica que o `ServiceReference1.ICalculator` contrato de serviço é usado para comunicação entre o cliente do WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="32a3c-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="32a3c-114">O canal do WCF é configurado com o sistema forneceu <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="32a3c-114">The WCF channel is configured with the system-provided <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="32a3c-115">Esse contrato foi gerado usando **adicionar referência de serviço** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32a3c-115">This contract was generated by using **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="32a3c-116">Ele é essencialmente uma cópia do contrato que foi definido no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="32a3c-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="32a3c-117">O <xref:System.ServiceModel.WSHttpBinding> associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="32a3c-117">The <xref:System.ServiceModel.WSHttpBinding> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

<span data-ttu-id="32a3c-118">Para obter mais informações sobre como usar o cliente gerado com essa configuração, consulte [como: Usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="32a3c-118">For more information about how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="32a3c-119">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="32a3c-119">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="32a3c-120">Como: Usar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="32a3c-120">How to: Use a WCF client</span></span>](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a><span data-ttu-id="32a3c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32a3c-121">See also</span></span>

- [<span data-ttu-id="32a3c-122">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="32a3c-122">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="32a3c-123">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="32a3c-123">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="32a3c-124">Como: Criar um cliente</span><span class="sxs-lookup"><span data-stu-id="32a3c-124">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="32a3c-125">Introdução</span><span class="sxs-lookup"><span data-stu-id="32a3c-125">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="32a3c-126">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="32a3c-126">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)