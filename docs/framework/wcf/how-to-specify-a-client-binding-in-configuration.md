---
title: Como especificar uma associação de cliente em configuração
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184046"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="5287d-102">Como especificar uma associação de cliente em configuração</span><span class="sxs-lookup"><span data-stu-id="5287d-102">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="5287d-103">Neste exemplo, um aplicativo de console cliente é criado para usar um serviço de calculadora, e a vinculação para esse cliente é especificada declarativamente na configuração.</span><span class="sxs-lookup"><span data-stu-id="5287d-103">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="5287d-104">O cliente acessa o `CalculatorService` `ICalculator` , que implementa a interface, <xref:System.ServiceModel.BasicHttpBinding> e tanto o serviço quanto o cliente usam a classe.</span><span class="sxs-lookup"><span data-stu-id="5287d-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="5287d-105">O procedimento descrito pressupõe que o serviço de calculadora está em execução.</span><span class="sxs-lookup"><span data-stu-id="5287d-105">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="5287d-106">Para obter informações sobre como construir o serviço, consulte [Como: Especificar uma vinculação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5287d-106">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="5287d-107">Ele também usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="5287d-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="5287d-108">A ferramenta gera o código e configuração do cliente para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5287d-108">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="5287d-109">O cliente é construído em duas partes.</span><span class="sxs-lookup"><span data-stu-id="5287d-109">The client is built in two parts.</span></span> <span data-ttu-id="5287d-110">Svcutil.exe gera `ClientCalculator` o que `ICalculator` implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="5287d-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="5287d-111">Este aplicativo cliente é então construído construindo `ClientCalculator`uma instância de .</span><span class="sxs-lookup"><span data-stu-id="5287d-111">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="5287d-112">Geralmente é a melhor prática para especificar as informações de vinculação e endereço declarativamente na configuração, em vez de imperativamente em código.</span><span class="sxs-lookup"><span data-stu-id="5287d-112">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="5287d-113">Definir pontos finais no código geralmente não é prático porque as vinculações e endereços de um serviço implantado são tipicamente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="5287d-113">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="5287d-114">De forma mais geral, manter as informações de vinculação e endereçamento fora do código permite que eles mudem sem ter que recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5287d-114">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="5287d-115">Você pode executar todas as seguintes etapas de configuração usando a [Ferramenta de Editor de Configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5287d-115">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="5287d-116">Para obter a cópia de origem deste exemplo, consulte a amostra [BasicBinding.](./samples/basicbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5287d-116">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="5287d-117">Especificando uma vinculação do cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="5287d-117">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="5287d-118">Use Svcutil.exe da linha de comando para gerar código a partir de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="5287d-118">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="5287d-119">O cliente gerado contém `ICalculator` a interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="5287d-119">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="5287d-120">O cliente gerado também contém `ClientCalculator`a implementação do .</span><span class="sxs-lookup"><span data-stu-id="5287d-120">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="5287d-121">Svcutil.exe também gera a configuração <xref:System.ServiceModel.BasicHttpBinding> para o cliente que usa a classe.</span><span class="sxs-lookup"><span data-stu-id="5287d-121">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="5287d-122">Ao usar o Visual Studio, nomeie este arquivo App.config. Observe que o endereço e as informações de vinculação não são especificados em nenhum lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="5287d-122">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="5287d-123">Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5287d-123">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="5287d-124">Crie uma instância `ClientCalculator` do em um aplicativo e, em seguida, chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="5287d-124">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="5287d-125">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="5287d-125">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5287d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="5287d-126">See also</span></span>

- [<span data-ttu-id="5287d-127">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5287d-127">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
