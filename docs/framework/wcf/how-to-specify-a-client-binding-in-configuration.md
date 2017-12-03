---
title: "Como especificar uma associação de cliente em configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9db5559df52d0da2ee75945a25c026dfc6169969
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="1421f-102">Como especificar uma associação de cliente em configuração</span><span class="sxs-lookup"><span data-stu-id="1421f-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="1421f-103">Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de cálculo e a associação para que o cliente é especificada declarativamente na configuração.</span><span class="sxs-lookup"><span data-stu-id="1421f-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="1421f-104">O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="1421f-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="1421f-105">O procedimento descrito assume que o serviço de cálculo é executada.</span><span class="sxs-lookup"><span data-stu-id="1421f-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="1421f-106">Para obter informações sobre como criar o serviço, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1421f-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="1421f-107">Ele também usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="1421f-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] provides to automatically generate the client components.</span></span> <span data-ttu-id="1421f-108">A ferramenta gera o código de cliente e configuração para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="1421f-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="1421f-109">O cliente é criado em duas partes.</span><span class="sxs-lookup"><span data-stu-id="1421f-109">The client is built in two parts.</span></span> <span data-ttu-id="1421f-110">Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="1421f-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="1421f-111">Este aplicativo cliente é construído, criando uma instância de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="1421f-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="1421f-112">Geralmente é a prática recomendada para especificar declarativamente a associação e as informações de endereço na configuração em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="1421f-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="1421f-113">Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="1421f-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="1421f-114">Geralmente, informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1421f-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="1421f-115">Você pode executar todas as seguintes etapas de configuração usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1421f-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="1421f-116">Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="1421f-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="1421f-117">Especificando uma associação na configuração de cliente</span><span class="sxs-lookup"><span data-stu-id="1421f-117">Specifying a client binding in configuration</span></span>  
  
1.  <span data-ttu-id="1421f-118">Use o Svcutil.exe da linha de comando para gerar o código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="1421f-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="1421f-119">O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="1421f-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  <span data-ttu-id="1421f-120">O cliente gerado também contém a implementação de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="1421f-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  <span data-ttu-id="1421f-121">Svcutil.exe também gera a configuração do cliente que usa o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="1421f-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="1421f-122">Ao usar [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], nomeie esse arquivo App. config. Observe que o endereço e as informações de associação não estão especificados em qualquer lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="1421f-122">When using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="1421f-123">Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1421f-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  <span data-ttu-id="1421f-124">Criar uma instância do `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="1421f-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  <span data-ttu-id="1421f-125">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="1421f-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1421f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1421f-126">See Also</span></span>  
 <span data-ttu-id="1421f-127">[Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) (Usando associações para configurar serviços e clientes)</span><span class="sxs-lookup"><span data-stu-id="1421f-127">[Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)</span></span>
