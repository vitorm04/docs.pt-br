---
title: Como especificar uma associação de cliente em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 3a05c60b6e68f87c31e74774bf0b50e535477b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="8f9af-102">Como especificar uma associação de cliente em código</span><span class="sxs-lookup"><span data-stu-id="8f9af-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="8f9af-103">Neste exemplo, um cliente é criado para usar um serviço de cálculo e a associação para esse cliente é especificada imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="8f9af-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="8f9af-104">O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="8f9af-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="8f9af-105">Este procedimento pressupõe que a Calculadora está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="8f9af-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="8f9af-106">Para obter informações sobre o serviço, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8f9af-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="8f9af-107">Ele também usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)fornece Windows Communication Foundation (WCF) para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="8f9af-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="8f9af-108">A ferramenta gera o código do cliente para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8f9af-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="8f9af-109">O cliente é criado em duas partes.</span><span class="sxs-lookup"><span data-stu-id="8f9af-109">The client is built in two parts.</span></span> <span data-ttu-id="8f9af-110">Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="8f9af-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="8f9af-111">Este aplicativo cliente é construído, criando uma instância de `ClientCalculator` e, em seguida, especificando a associação e o endereço para o serviço no código.</span><span class="sxs-lookup"><span data-stu-id="8f9af-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="8f9af-112">Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="8f9af-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="8f9af-113">Para especificar uma associação personalizada em código</span><span class="sxs-lookup"><span data-stu-id="8f9af-113">To specify a custom binding in code</span></span>  
  
1.  <span data-ttu-id="8f9af-114">Use o Svcutil.exe da linha de comando para gerar o código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="8f9af-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  <span data-ttu-id="8f9af-115">O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="8f9af-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  <span data-ttu-id="8f9af-116">O cliente gerado também contém a implementação de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="8f9af-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  <span data-ttu-id="8f9af-117">Criar uma instância do `ClientCalculator` que usa o <xref:System.ServiceModel.BasicHttpBinding> de classe em um aplicativo cliente e, em seguida, chamar as operações de serviço no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="8f9af-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  <span data-ttu-id="8f9af-118">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="8f9af-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9af-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f9af-119">See Also</span></span>  
 [<span data-ttu-id="8f9af-120">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8f9af-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
