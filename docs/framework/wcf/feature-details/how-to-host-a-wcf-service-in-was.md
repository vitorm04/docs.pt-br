---
title: Como hospedar um serviço do WCF em WAS
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4613587d829b082ee7182cc32e34d2d2d563241
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="dbd77-102">Como hospedar um serviço do WCF em WAS</span><span class="sxs-lookup"><span data-stu-id="dbd77-102">How to: Host a WCF Service in WAS</span></span>
<span data-ttu-id="dbd77-103">Este tópico descreve as etapas básicas necessárias para criar um serviços de ativação de processos do Windows (também conhecido como WAS) hospedado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="dbd77-104">FOI é o novo serviço de ativação de processo é uma generalização dos recursos de serviços de informações da Internet (IIS) que funcionam com protocolos de transporte não HTTP.</span><span class="sxs-lookup"><span data-stu-id="dbd77-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dbd77-105"> usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas nos protocolos não HTTP com suporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], como TCP, pipes nomeados e enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="dbd77-105"> uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="dbd77-106">Essa opção de hospedagem requer que os componentes de ativação do WAS são instalados e configurados corretamente, mas não exige qualquer código de hospedagem para ser gravado como parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbd77-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="dbd77-107">Para obter mais informações sobre como instalar e configurar o WAS, consulte [como: instalar e configurar componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span><span class="sxs-lookup"><span data-stu-id="dbd77-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="dbd77-108">Não foi oferece suporte à ativação se o pipeline de processamento de solicitação do servidor web está definido para o modo clássico.</span><span class="sxs-lookup"><span data-stu-id="dbd77-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="dbd77-109">Pipeline de processamento de solicitação do servidor web deve ser definido para o modo integrado se a ativação do WAS será usado.</span><span class="sxs-lookup"><span data-stu-id="dbd77-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="dbd77-110">Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado no WAS, as associações padrão são usadas como de costume.</span><span class="sxs-lookup"><span data-stu-id="dbd77-110">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="dbd77-111">No entanto, ao usar o <xref:System.ServiceModel.NetTcpBinding> e <xref:System.ServiceModel.NetNamedPipeBinding> para configurar um serviço hospedado do WAS, uma restrição deve ser atendida.</span><span class="sxs-lookup"><span data-stu-id="dbd77-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="dbd77-112">Quando diferentes pontos de extremidade usam o mesmo transporte, as configurações de associação tem que corresponder as sete propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="dbd77-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
-   <span data-ttu-id="dbd77-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="dbd77-113">ConnectionBufferSize</span></span>  
  
-   <span data-ttu-id="dbd77-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="dbd77-114">ChannelInitializationTimeout</span></span>  
  
-   <span data-ttu-id="dbd77-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="dbd77-115">MaxPendingConnections</span></span>  
  
-   <span data-ttu-id="dbd77-116">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="dbd77-116">MaxOutputDelay</span></span>  
  
-   <span data-ttu-id="dbd77-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="dbd77-117">MaxPendingAccepts</span></span>  
  
-   <span data-ttu-id="dbd77-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="dbd77-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
-   <span data-ttu-id="dbd77-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="dbd77-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="dbd77-120">Caso contrário, o ponto de extremidade é inicializado pela primeira vez sempre determina os valores dessas propriedades e pontos de extremidade adicionados posteriormente lançam um <xref:System.ServiceModel.ServiceActivationException> se elas não corresponderem a essas configurações.</span><span class="sxs-lookup"><span data-stu-id="dbd77-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="dbd77-121">Para a cópia de origem deste exemplo, consulte [ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md).</span><span class="sxs-lookup"><span data-stu-id="dbd77-121">For the source copy of this example, see [TCP Activation](../../../../docs/framework/wcf/samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="dbd77-122">Para criar um serviço básico hospedado pelo WAS</span><span class="sxs-lookup"><span data-stu-id="dbd77-122">To create a basic service hosted by WAS</span></span>  
  
1.  <span data-ttu-id="dbd77-123">Defina um contrato de serviço para o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  <span data-ttu-id="dbd77-124">Implemente o contrato de serviço em uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="dbd77-125">Observe que as informações de endereço e associação não são especificadas dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="dbd77-126">Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dbd77-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  <span data-ttu-id="dbd77-127">Criar um arquivo Web. config para definir o <xref:System.ServiceModel.NetTcpBinding> associação a ser usado pelo `CalculatorService` pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dbd77-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
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
  
4.  <span data-ttu-id="dbd77-128">Crie um arquivo SVC que contém o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="dbd77-128">Create a Service.svc file that contains the following code.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  <span data-ttu-id="dbd77-129">Coloque o arquivo svc no diretório virtual do IIS.</span><span class="sxs-lookup"><span data-stu-id="dbd77-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="dbd77-130">Para criar um cliente para usar o serviço</span><span class="sxs-lookup"><span data-stu-id="dbd77-130">To create a client to use the service</span></span>  
  
1.  <span data-ttu-id="dbd77-131">Use [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="dbd77-132">O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="dbd77-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  <span data-ttu-id="dbd77-133">O aplicativo cliente gerado também contém a implementação de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="dbd77-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="dbd77-134">Observe que as informações de endereço e associação não são especificadas em qualquer lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="dbd77-135">Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dbd77-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  <span data-ttu-id="dbd77-136">A configuração do cliente que usa o <xref:System.ServiceModel.NetTcpBinding> também é gerado pelo Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="dbd77-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="dbd77-137">Este arquivo deve ser nomeado no arquivo App. config quando usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbd77-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  <span data-ttu-id="dbd77-138">Criar uma instância do `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbd77-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  <span data-ttu-id="dbd77-139">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="dbd77-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd77-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbd77-140">See Also</span></span>  
 [<span data-ttu-id="dbd77-141">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="dbd77-141">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="dbd77-142">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="dbd77-142">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
