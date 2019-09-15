---
title: 'Como: especificar uma associação de cliente na configuração'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 0757dac4cdcffc7c3550432a71fe45b587327660
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990223"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="8191d-102">Como: especificar uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="8191d-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="8191d-103">Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de calculadora e a associação para esse cliente é especificada declarativamente na configuração.</span><span class="sxs-lookup"><span data-stu-id="8191d-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="8191d-104">O cliente acessa o `CalculatorService`, que implementa a `ICalculator` interface, e o serviço e o cliente usam a <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="8191d-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="8191d-105">O procedimento descrito pressupõe que o serviço de calculadora está em execução.</span><span class="sxs-lookup"><span data-stu-id="8191d-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="8191d-106">Para obter informações sobre como criar o serviço, consulte [como: Especifique uma associação de serviço na](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.</span><span class="sxs-lookup"><span data-stu-id="8191d-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="8191d-107">Ele também usa a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="8191d-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="8191d-108">A ferramenta gera o código do cliente e a configuração para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8191d-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="8191d-109">O cliente é criado em duas partes.</span><span class="sxs-lookup"><span data-stu-id="8191d-109">The client is built in two parts.</span></span> <span data-ttu-id="8191d-110">Svcutil. exe gera o `ClientCalculator` que implementa a `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="8191d-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="8191d-111">Esse aplicativo cliente é então construído pela construção de uma instância do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8191d-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="8191d-112">Geralmente, é a prática recomendada especificar a associação e as informações de endereço de forma declarativa na configuração, em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="8191d-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="8191d-113">A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="8191d-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="8191d-114">Em geral, manter as informações de vinculação e endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8191d-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="8191d-115">Você pode executar todas as etapas de configuração a seguir usando a [ferramenta do editor de configuração (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8191d-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="8191d-116">Para a cópia de origem deste exemplo, consulte o exemplo de [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8191d-116">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="8191d-117">Especificando uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="8191d-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="8191d-118">Use svcutil. exe da linha de comando para gerar código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="8191d-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="8191d-119">O cliente gerado contém a `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="8191d-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="8191d-120">O cliente gerado também contém a implementação do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8191d-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="8191d-121">Svcutil. exe também gera a configuração para o cliente que usa a <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="8191d-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="8191d-122">Ao usar o Visual Studio, nomeie esse arquivo app. config. Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="8191d-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="8191d-123">Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8191d-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. <span data-ttu-id="8191d-124">Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="8191d-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="8191d-125">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="8191d-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8191d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8191d-126">See also</span></span>

- [<span data-ttu-id="8191d-127">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8191d-127">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
