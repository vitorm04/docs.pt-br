---
title: Como especificar uma associação de cliente em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184050"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="6eb4d-102">Como especificar uma associação de cliente em código</span><span class="sxs-lookup"><span data-stu-id="6eb4d-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="6eb4d-103">Neste exemplo, um cliente é criado para usar um serviço de calculadora e a vinculação para esse cliente é especificada imperativamente em código.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="6eb4d-104">O cliente acessa o `CalculatorService` `ICalculator` , que implementa a interface, <xref:System.ServiceModel.BasicHttpBinding> e tanto o serviço quanto o cliente usam a classe.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="6eb4d-105">Este procedimento pressupõe que o serviço de calculadora está em execução.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="6eb4d-106">Para obter informações sobre a construção do serviço, consulte [Como: Especificar uma vinculação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6eb4d-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="6eb4d-107">Ele também usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="6eb4d-108">A ferramenta gera o código do cliente para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="6eb4d-109">O cliente é construído em duas partes.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-109">The client is built in two parts.</span></span> <span data-ttu-id="6eb4d-110">Svcutil.exe gera `ClientCalculator` o que `ICalculator` implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="6eb4d-111">Esse aplicativo cliente é então construído construindo `ClientCalculator` uma instância e, em seguida, especificando a vinculação e o endereço para o serviço em código.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="6eb4d-112">Para obter a cópia de origem deste exemplo, consulte a amostra [BasicBinding.](./samples/basicbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6eb4d-112">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="6eb4d-113">Para especificar uma vinculação personalizada em código</span><span class="sxs-lookup"><span data-stu-id="6eb4d-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="6eb4d-114">Use Svcutil.exe da linha de comando para gerar código a partir de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="6eb4d-115">O cliente gerado contém `ICalculator` a interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="6eb4d-116">O cliente gerado também contém `ClientCalculator`a implementação do .</span><span class="sxs-lookup"><span data-stu-id="6eb4d-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="6eb4d-117">Crie uma instância `ClientCalculator` do <xref:System.ServiceModel.BasicHttpBinding> que usa a classe em um aplicativo cliente e, em seguida, chame as operações de serviço no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="6eb4d-118">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="6eb4d-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb4d-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="6eb4d-119">See also</span></span>

- [<span data-ttu-id="6eb4d-120">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6eb4d-120">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
