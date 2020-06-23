---
title: Como especificar uma associação de cliente em configuração
description: Saiba como especificar a associação para um cliente WCF declarativamente em um arquivo de configuração. O cliente acessa um serviço neste exemplo.
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244485"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="71d86-104">Como especificar uma associação de cliente em configuração</span><span class="sxs-lookup"><span data-stu-id="71d86-104">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="71d86-105">Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de calculadora e a associação para esse cliente é especificada declarativamente na configuração.</span><span class="sxs-lookup"><span data-stu-id="71d86-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="71d86-106">O cliente acessa o `CalculatorService` , que implementa a `ICalculator` interface, e o serviço e o cliente usam a <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="71d86-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="71d86-107">O procedimento descrito pressupõe que o serviço de calculadora está em execução.</span><span class="sxs-lookup"><span data-stu-id="71d86-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="71d86-108">Para obter informações sobre como criar o serviço, consulte [como especificar uma associação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="71d86-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="71d86-109">Ele também usa a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="71d86-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="71d86-110">A ferramenta gera o código do cliente e a configuração para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="71d86-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="71d86-111">O cliente é criado em duas partes.</span><span class="sxs-lookup"><span data-stu-id="71d86-111">The client is built in two parts.</span></span> <span data-ttu-id="71d86-112">Svcutil.exe gera o `ClientCalculator` que implementa a `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="71d86-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="71d86-113">Esse aplicativo cliente é então construído pela construção de uma instância do `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="71d86-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="71d86-114">Geralmente, é a prática recomendada especificar a associação e as informações de endereço de forma declarativa na configuração, em vez de imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="71d86-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="71d86-115">A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="71d86-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="71d86-116">Em geral, manter as informações de vinculação e endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar ou reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71d86-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="71d86-117">Você pode executar todas as etapas de configuração a seguir usando a [ferramenta do editor de configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="71d86-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="71d86-118">Para a cópia de origem deste exemplo, consulte o exemplo de [BasicBinding](./samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="71d86-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="71d86-119">Especificando uma associação de cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="71d86-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="71d86-120">Use Svcutil.exe da linha de comando para gerar código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="71d86-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="71d86-121">O cliente gerado contém a `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="71d86-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="71d86-122">O cliente gerado também contém a implementação do `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="71d86-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="71d86-123">Svcutil.exe também gera a configuração para o cliente que usa a <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="71d86-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="71d86-124">Ao usar o Visual Studio, nomeie esse arquivo App.config. Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="71d86-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="71d86-125">Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="71d86-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="71d86-126">Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="71d86-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="71d86-127">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="71d86-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d86-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="71d86-128">See also</span></span>

- [<span data-ttu-id="71d86-129">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="71d86-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
