---
title: Como hospedar um serviço do WCF em WAS
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 40460baeb136345f2532ec6ad5035bd5d3a40254
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051981"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="73859-102">Como hospedar um serviço do WCF em WAS</span><span class="sxs-lookup"><span data-stu-id="73859-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="73859-103">Este tópico descreve as etapas básicas necessárias para criar um serviço do Windows Process Activation Services (também conhecido como WAS) hospedado Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="73859-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="73859-104">O WAS é o novo serviço de ativação de processos que é uma generalização dos recursos de Serviços de Informações da Internet (IIS) que funciona com protocolos de transporte não HTTP.</span><span class="sxs-lookup"><span data-stu-id="73859-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="73859-105">O WCF usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas nos protocolos não HTTP com suporte do WCF, como TCP, pipes nomeados e enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="73859-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="73859-106">Essa opção de hospedagem requer que os componentes WAS de ativação sejam instalados e configurados corretamente, mas não exige que nenhum código de hospedagem seja gravado como parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73859-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="73859-107">Para obter mais informações sobre como instalar e configurar o WAS, consulte [como instalar e configurar componentes de ativação do WCF](how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="73859-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="73859-108">A ativação do WAS não terá suporte se o pipeline de processamento de solicitação do servidor Web estiver definido para o modo clássico.</span><span class="sxs-lookup"><span data-stu-id="73859-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="73859-109">O pipeline de processamento de solicitações do servidor Web deverá ser definido como modo integrado se a ativação do WAS for usada.</span><span class="sxs-lookup"><span data-stu-id="73859-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="73859-110">Quando um serviço WCF é hospedado no WAS, as associações padrão são usadas da maneira usual.</span><span class="sxs-lookup"><span data-stu-id="73859-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="73859-111">No entanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> e o <xref:System.ServiceModel.NetNamedPipeBinding> para configurar um serviço was hospedado, uma restrição deve ser satisfeita.</span><span class="sxs-lookup"><span data-stu-id="73859-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="73859-112">Quando pontos de extremidade diferentes usam o mesmo transporte, as configurações de associação precisam corresponder às sete Propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="73859-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="73859-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="73859-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="73859-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="73859-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="73859-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="73859-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="73859-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="73859-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="73859-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="73859-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="73859-118">ConnectionPoolSettings. IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="73859-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="73859-119">ConnectionPoolSettings. MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="73859-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="73859-120">Caso contrário, o ponto de extremidade que é inicializado primeiro sempre determina os valores dessas propriedades, e os pontos de extremidade adicionados posteriormente lançam um <xref:System.ServiceModel.ServiceActivationException> se não corresponderem a essas configurações.</span><span class="sxs-lookup"><span data-stu-id="73859-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="73859-121">Para a cópia de origem deste exemplo, consulte [ativação TCP](../samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="73859-121">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="73859-122">Para criar um serviço básico hospedado pelo WAS</span><span class="sxs-lookup"><span data-stu-id="73859-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="73859-123">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="73859-124">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="73859-125">Observe que as informações de endereço ou de associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="73859-126">Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="73859-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="73859-127">Crie um arquivo de Web.config para definir a <xref:System.ServiceModel.NetTcpBinding> associação a ser usada pelos `CalculatorService` pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="73859-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="73859-128">Crie um arquivo Service. svc que contenha o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="73859-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="73859-129">Coloque o arquivo Service. svc em seu diretório virtual do IIS.</span><span class="sxs-lookup"><span data-stu-id="73859-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="73859-130">Para criar um cliente para usar o serviço</span><span class="sxs-lookup"><span data-stu-id="73859-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="73859-131">Use a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="73859-132">O cliente gerado contém a `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="73859-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="73859-133">O aplicativo cliente gerado também contém a implementação do `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="73859-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="73859-134">Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="73859-135">Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="73859-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="73859-136">A configuração do cliente que usa o <xref:System.ServiceModel.NetTcpBinding> também é gerada pelo Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="73859-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="73859-137">Esse arquivo deve ser nomeado no arquivo de App.config ao usar o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73859-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="73859-138">Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="73859-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="73859-139">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="73859-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73859-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="73859-140">See also</span></span>

- [<span data-ttu-id="73859-141">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="73859-141">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="73859-142">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="73859-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
